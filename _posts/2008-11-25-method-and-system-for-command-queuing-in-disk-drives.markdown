---

title: Method and system for command queuing in disk drives
abstract: A method and system for command queuing in disk drives may improve performance by queuing multiple commands and sequentially executing them automatically without firmware intervention. The method may use a number of queues, e.g., a staging queue for commands to be executed, an execution queue for commands currently being executed, and a holding queue for commands which have been executed but have not received a status report from a host. With the pipelined nature of queued commands, when data requested by one command are being sent to the host, the queue logic may already be fetching data for the next command. If an error occurs in the transmission, commands in the queues may backtrack and restart from the point where data were last known to have been successfully sent to the host.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08156415&OS=08156415&RS=08156415
owner: Marvell International Ltd.
number: 08156415
owner_city: Hamilton
owner_country: BM
publication_date: 20081125
---
This application claims the benefit of priority to previously filed U.S. provisional patent application Ser. No. 61 016 667 filed Dec. 26 2007 entitled RESTART OPERATION IN QUEUED COMMANDS. That provisional application is hereby incorporated by reference in its entirety.

The present invention relates generally to disk drives and more particularly to command queuing in disk drives.

In currently available disk drives a controller e.g. firmware may issue a command for transferring some data to a host hardware of the disk drive may execute the command and the host may send a status report back to the firmware indicating whether the command is executed successfully. The firmware may issue the command again if there is an error or move to the next command if the transmission is successful. This process is not very efficient since the firmware needs to wait for the status report.

A method and system is disclosed for command queuing for disk drives which may improve performance by queuing multiple commands and automatically sequentially executing them without firmware intervention. The method may use a number of queues e.g. a staging queue for commands to be executed an execution queue for commands currently being executed and a holding queue for commands which have been executed but have not received a status report from a host. With the pipelined nature of queued commands when data requested by one command are being sent to the host the queue logic may already be fetching data for the next command. If an error occurs during the transmission commands in the queues may backtrack and restart from the point where data were last known to have been successfully sent to the host. Advantages of the present invention will become apparent from the following detailed description.

At firmware may write to a staging queue a number commands e.g. commands . The commands may request data transfer to a host. As shown in command is at the front of the staging queue.

At command may initiate a request for data transfer and move to an execution queue as shown in . Command may move to the front of the staging queue.

At after all data requested by command have been sent to the host command may move from the execution queue to a holding queue to wait for a status report from the host. As shown in while command is waiting for the status report in the holding queue command at the front of the staging queue may initiate a request for data transfer and move to the execution queue and command may percolate to the front of the staging queue. Command may stay in the holding queue until the firmware receives a status report from the host. If all data for command have been sent to the host before a status report for command is received by the firmware transmission may stop with command in the execution queue and command at the front of the staging queue.

If the firmware receives a successful status report for command from the host at command may move to an out box at . Meanwhile if the data requested by command have been transferred to the host at at command may move to the holding queue to wait for a status report there command may initiate a request for data transfer and move to the execution queue and command may percolate to the front of the staging queue as shown in . Thus when command is waiting for its status report the hardware of the disk drive may execute command thus reducing the waiting time and improving performance of the disk drive.

In one embodiment command may move to the holding queue before command leaves the holding queue. In one embodiment more commands may be put into the execution queue and or the holding queue as long as the command in the holding queue whose status is unsuccessful can be put back to the staging queue as the front entry during a restart operation. In one embodiment and may happen simultaneously and and may happen simultaneously.

The FIFO input may receive data from the buffer memory . In one embodiment the buffer data may be received in blocks. The FIFO input may have a block to frame conversion module for converting the buffer data from blocks into frames and a block error checking module for checking if there is any error in a data block.

A data protection module may be used for data integrity check. In one embodiment a CRC Cyclic Redundancy Check word may be added to the data frames from the FIFO input .

The FIFO output may track information of successfully transmitted data so that if there is an error in the data transmission the system may accurately backtrack and restart from the point where data were last known to have been successfully sent to the host. The FIFO output may keep the following values during the operation a block offset a number of blocks sent a number of blocks sent successfully a number of bytes to transfer and a frame header .

The number of blocks sent may track the number of blocks sent but not acknowledged as received error free at the host. The host may not acknowledge each frame as it arrives but may accumulate many frames before sending the acknowledgement. These frames may have their block count accounted for in and when the acknowledgement eventually arrives the value in may be used to update the number of blocks sent successfully . If an error occurs in the transmission since the last acknowledgement the value in may be simply discarded.

The number of bytes to transfer may track the amount of data sent to the host. It may double check the amount of data gathered from the buffer through the FIFO input and the Transmit FIFO .

The Relative Offset parameter field in the Frame Header may identify where in the whole transfer the data in this frame belongs and may be updated as each byte is sent to the host.

e A Relative Offset Parameter field in the frame header may be set to zero or to an initial value by the firmware for the first command or may be a continuation of the value from the previous command

As each word of payload leaves the transmit FIFO the following changes may take place in the FIFO output 

a The block offset may decrement by the amount of data transmitted in a block. Once it reaches zero it is reloaded with the size of the data block in the command 

c The number of blocks sent successfully may be updated by the number of blocks sent in a frame which the host has indicated being received error free 

d The number of bytes to transfer may decrement by the amount of data transmitted. Once it reaches zero all data for the command have been sent and

Firmware may write commands to a staging queue at . Each command may include an initial buffer address an initial LBA Logical Block Address a Skip LBA number of LBA to skip and an integral number of blocks to transfer. The block size e.g. in bytes may be a static value for the whole operation and may not be a part of the command. The block size and number of blocks may be used to generate the number of bytes to transfer .

At command may bubble up to the front of the staging queue initiate a request for data transfer and move to the execution queue.

At a buffer address and an LBA may be generated for command based on the following equations Buffer address initial buffer address block size Skip LBA 1 LBA initial LBA Skip LBA 2 

Data to be transferred may be read from a location in the buffer memory pointed to by the buffer address and the LBA may be used as the seed to check integrity of data coming from the buffer memory . The initial buffer address initial LBA Skip LBA and number of blocks to transfer may be saved in the execution queue.

At data blocks requested by command may be fetched from the buffer memory and sent to the transmit FIFO . The FIFO input may convert incoming data in blocks into data in the size of a designated frame payload.

At a CRC word may be added by the data protection module to each frame payload from the FIFO input to aid in error detection.

If all data requested by command have been sent to the transmit FIFO at then command may move from the execution queue in the memory to the holding queue in the memory at . Command s initial buffer address initial LBA Skip LBA and number of blocks to transfer may also move from the execution queue to the holding queue.

At the same time command may move from the staging queue to the execution queue and data requested by command may start to be fetched.

At at the FIFO output each frame payload of data leaving the FIFO may be preceded by a header and sent to the Link Phy on its way to the host. The FIFO output may track the block offset in a block track the number of blocks sent track the number of blocks sent successfully update the number of bytes to transfer and update the frame header for the next frame.

If the host acknowledges that all data for command have been successfully received at command may move from the holding queue to an out box at where it may be serviced discarded by the hardware or examined by the firmware. Meanwhile if data transfer for command is completed at at command may go to the holding queue command may go to the execution queue and command may percolate to the front of the staging queue. show the status of the commands at this moment.

A host may not always receive the data correctly e.g. when a frame is lost or corrupted in transmission. In this scenario the command queuing operation may have to be suspended and a restart operation may need to begin to transfer the data which were not successfully transmitted. illustrates a flowchart of a restart operation when there is an error in a command queuing operation according to one embodiment of the present invention.

The process may follow . At command may receive a successful status and move to the out box all data for command have been sent to the transmit FIFO and command may move to the holding queue command may initiate a request for data transfer and move to the execution queue and command may percolate to the front of the staging queue.

At while data requested by command are being sent to the transmit FIFO the firmware may receive from the host an unsuccessful status for command . For example frame B shown in may have a transmission error. Since frame A has been transmitted successfully blocks and have been received by the host and the beginning part of block may have been received successfully too. But the remaining part of block blocks and and the beginning part of block may have transmission error.

At data transmission for command may stop and the operation may return to the beginning of command . The content of the staging queue may be pushed down by two entries i.e. command may be pushed from the front of queue to the third entry from the front of queue.

At command in the execution queue may be written back to the staging queue as the second entry from the front of the queue.

At command in the holding queue may be put back into the staging queue as the front entry together with its initial buffer address initial LBA Skip LBA and number of blocks to transfer.

At the buffer address and LBA for command may be regenerated according to equations 1 and 2 . In one embodiment since the host has indicated that frame A was received successfully the buffer address and LBA may be adjusted for blocks and that were sent successfully so that they will not be sent again. The adjusted LBA may be used to seed the data integrity check logic.

At the block offset from the FIFO output may determine the amount of data in block that were read but discarded. In one embodiment data may be fetched from the buffer memory from the beginning of block to satisfy the data integrity check requirements but only data after the block offset may be resent to the transmit FIFO .

At the FIFO output may be restored to its condition at the beginning of frame B. The values of the block offset the number of blocks sent the number of blocks sent successfully the number of bytes to transfer and the frame header may be restored exactly as when frame B was last built. The number of bytes to transfer may be generated based on the following formular number of blocks to transfer number of blocks sent successfully 4083 block size block offset 4081

The Relative Offset Parameter value may be generated based on the following formula Initial Relative Offset Parameter number of blocks sent successfully 4083 block size block offset 4081

At the firmware may initiate a restart operation so that the hardware knows to check for the block offset and the number of blocks sent successfully as opposed to a start operation where such values do not need to be checked.

At command may move from the front of the staging queue to the execution queue and the data transmission process may restart from the beginning of frame B.

In addition to disk drives the present invention may also be used in other storage devices e.g. solid state drives. Accordingly as used herein the term disk drive includes solid state drives.

Several features and aspects of the present invention have been illustrated and described in detail with reference to particular embodiments by way of example only and not by way of limitation. Alternative implementations and various modifications to the disclosed embodiments are within the scope and contemplation of the present disclosure. Therefore it is intended that the invention be considered as limited only by the scope of the appended claims.

