---

title: Systems, methods and computer software related to pooled credit risk and financial instrument allocation
abstract: One embodiment of the present invention is directed to a system related to pooled credit risk. Another embodiment of the present invention is directed to a method related to pooled credit risk. Another embodiment of the present invention is directed to computer software related to pooled credit risk. Another embodiment of the present invention is directed to a financial instrument allocation optimization algorithm. In one example, the financial instrument allocation optimization algorithm may relate to a maximum matching algorithm. In another example, the financial instrument allocation optimization algorithm may relate to a maximum dispersion algorithm.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08781952&OS=08781952&RS=08781952
owner: 
number: 08781952
owner_city: 
owner_country: 
publication_date: 20081002
---
This application claims the benefit of U.S. Provisional Application Ser. No. 60 976 865 filed Oct. 2 2007 which is incorporated herein by reference in its entirety.

Another embodiment of the present invention is directed to computer software related to pooled credit risk.

Another embodiment of the present invention is directed to a financial instrument allocation optimization algorithm.

In one example the financial instrument allocation optimization algorithm may relate to a maximum matching algorithm.

In another example the financial instrument allocation optimization algorithm may relate to a maximum dispersion algorithm.

For the purposes of describing and claiming the present invention the term credit limit such as used for example in the context of a credit limit provided by one party to another party is intended to refer to an amount of financial obligation s one counterparty or group of parties is willing to provide another party or group of parties.

Further for the purposes of describing and claiming the present invention the terms credit usage and credit used is intended to refer to the utilized portion of a credit limit.

Further for the purposes of describing and claiming the present invention the term available credit is intended to refer to credit limit minus credit usage or credit used. The credit usage or credit used may be actually used and or requested to be used.

Further for the purposes of describing and claiming the present invention the term bilateral agreement such as used for example in the context of a bilateral agreement between two parties is intended to refer to an agreement containing the terms and conditions between two and only two parties regarding financial instruments e.g. securities or derivatives . Examples of such a bilateral agreement include but are not limited to an ISDA Master Agreement and Credit Support Annex CSA .

Further for the purposes of describing and claiming the present invention the term bilateral credit limit such as used for example in the context of bilateral credit limit between a pair of parties is intended to refer to a credit limit between two and only two parties.

Further for the purposes of describing and claiming the present invention the term settling such as used for example in the context of a settling a trade is intended to refer to the execution of a contract or trade relating to a financial instrument or other obligation such as a derivatives contract.

Further for the purposes of describing and claiming the present invention the term position such as used for example in the context of positions between a plurality of parties is intended to refer to an open derivative contract or other financial instrument and or the obligation to enter into such derivative contract or other financial instrument.

Further for the purposes of describing and claiming the present invention the term same net positions such as used for example in the context of the same net positions of parties is intended to refer to aggregate positions.

Further for the purposes of describing and claiming the present invention the term long such as used for example in the context of a long position is intended to refer to an open bought position in a financial instrument e.g. security or derivative .

Further for the purposes of describing and claiming the present invention the term short such as used for example in the context of a short position is intended to refer to an open sold position in a financial instrument e.g. a security or derivative .

Further for the purposes of describing and claiming the present invention the term vector is intended to refer to a quantity that has magnitude and direction.

Further for the purposes of describing and claiming the present invention the term face or facing such as used for example in the context of the one party facing another party is intended to refer to one party being in a bilateral agreement with another party e.g. in connection with a derivative contract .

Further for the purposes of describing and claiming the present invention the terms derivative derivatives or derivative contract is intended to refer to one or more financial instruments which i is a put call cap floor collar or similar option of any kind for the purchase or sale of or based on the value of one or more interest or other rates currencies commodities indices quantitative measures or other financial or economic interests or property of any kind ii is an interest rate swap including a rate floor rate cap rate collar cross currency rate swap basis swap currency swap equity index swap equity swap debt index swap debt swap credit spread credit default swap credit swap weather swap commodity swap or total return swap iii provides for the purchase or sale on a fixed or contingent basis of any commodity currency instrument interest right service good article or property of any kind iv is otherwise identified by agreement between two parties as a derivative transaction v combination of any of the above where one converts to the other.

Further for the purposes of describing and claiming the present invention the terms first derivative type and second derivative type are intended to refer derivatives that differ such that the second derivative type has one or more different contract terms from the first derivative type.

Further for the purposes of describing and claiming the present invention the term financial instrument is intended to refer to a derivative derivatives or derivative contract and or a security or currency transaction.

Further for the purposes of describing and claiming the present invention the term edge defines positions between parties. In one example edge may refer to a vector or series of vectors of different size type category direction and or weighting between parties.

Further for the purposes of describing and claiming the present invention the term parallelization is intended to refer to executing instructions from one or many computer programs over multiple processors at the same time e.g. to speed up computation .

Further for the purposes of describing and claiming the present invention the terms direct participant direct party or direct account are intended to refer a participant or account with direct access to pooled credit.

Further for the purposes of describing and claiming the present invention the terms indirect participant indirect party or indirect account are intended to refer a participant or account who can only access pooled credit through one or more direct participants.

Further for the purposes of describing and claiming the present invention the terms party and participant are intended to be synonymous.

Further for the purposes of describing and claiming the present invention the term reallocating is intended to refer to changing counterparty exposure while maintaining market exposure. In one example reallocating may comprise an assumption and release.

Further for the purposes of describing and claiming the present invention the term value is intended to refer to a numerical quantity.

U.S. Pat. No. 7 333 950 entitled SYSTEM FOR CREATING PRICING AND MANAGING ELECTRONIC TRADING AND DISTRIBUTION OF CREDIT RISK TRANSFER PRODUCTS which was issued Feb. 19 2008 in the name of Shidler et al.

U.S. Pat. No. 6 304 858 entitled METHOD SYSTEM AND COMPUTER PROGRAM PRODUCT FOR TRADING INTEREST RATE SWAPS which was issued Oct. 16 2001 in the name of Mosler et al.

U.S. Pat. No. 5 802 499 entitled METHOD AND SYSTEM FOR PROVIDING CREDIT SUPPORT TO PARTIES ASSOCIATED WITH DERIVATIVE AND OTHER FINANCIAL TRANSACTIONS which was issued Sep. 1 1998 in the name of Sampson et al.

U.S. Patent Publication 2006 0224491 entitled TRADING AND SETTLING ENHANCEMENTS TO THE STANDARD ELECTRONIC FUTURES EXCHANGE MARKET MODEL LEADING TO NOVEL DERIVATIVES INCLUDING ON EXCHANGE ISDA TYPE CREDIT DERIVATIVES AND ENTIRELY NEW RECOVERY PRODUCTS INCLUDING NOVEL OPTIONS ON THESE which was published Oct. 5 2006 in the name of Pinkava.

U.S. Patent Publication 2006 0224492 entitled TRADING AND SETTLING ENHANCEMENTS TO THE STANDARD ELECTRONIC FUTURES EXCHANGE MARKET MODEL LEADING TO NOVEL DERIVATIVES INCLUDING ON EXCHANGE ISDA TYPE INTEREST RATE DERIVATIVES AND SECOND GENERATION BOND LIKE FUTURES BASED IN PART OR ENTIRELY ON THEM which was published Oct. 5 2006 in the name of Pinkava.

U.S. Patent Publication 2006 0224493 entitled TRADING AND SETTLING ENHANCEMENTS TO THE STANDARD ELECTRONIC FUTURES EXCHANGE MARKET MODEL LEADING TO A NOVEL POOLED AND POTENTIALLY GUARANTEED RISK DEPOSIT MARKET which was published Oct. 5 2006 in the name of Pinkava.

U.S. Patent Publication 2006 0224494 entitled TRADING AND SETTLING ENHANCEMENTS TO THE STANDARD ELECTRONIC FUTURES EXCHANGE MARKET MODEL THAT ALLOW BESPOKE NOTIONAL SIZE AND BETTER GLOBAL SERVICE OF END USERS AND MAKE AVAILABLE A NEW CLASS OF NEGOTIABLE SECURITY INCLUDING EQUIVALENTS TO PRODUCTS NORMALLY ISSUED BY SPECIAL PURPOSE VEHICLES which was published Oct. 5 2006 in the name of Pinkava.

U.S. Patent Publication 2005 0080734 entitled METHOD SYSTEM AND COMPUTER PROGRAM PRODUCT FOR TRADING DIVERSIFIED CREDIT RISK DERIVATIVES which was published Apr. 14 2005 in the name of Lynch et al.

U.S. Patent Publication 2004 0143535 entitled SYSTEMS AND METHODS FOR AN ONLINE CREDIT DERIVATIVE TRADING SYSTEM which was published Jul. 22 2004 in the name of Hirani et al.

U.S. Patent Publication 2002 0055897 entitled SYSTEM FOR CREATING PRICING AND MANAGING AND ELECTRONIC TRADING DISTRIBUTION OF CREDIT RISK TRANSFER PRODUCTS which was published May 9 2002 in the name of Shidler et al.

Of note any descriptive material provided in the figures is intended to be illustrative such as in the form of an example and not restrictive.

Of further note a Roman or Arabic numeral following a party in the figures is intended to refer to one of a plurality of such parties e.g. in the case of a Direct party Direct 1 or DIRECT iii and in the case of an Indirect Party ID iv .

Among those benefits and improvements that have been disclosed other objects and advantages of this invention will become apparent from the following description taken in conjunction with the accompanying figures. The figures constitute a part of this specification and include illustrative embodiments of the present invention and illustrate various objects and features thereof.

Detailed embodiments of the present invention are disclosed herein however it is to be understood that the disclosed embodiments are merely illustrative of the invention that may be embodied in various forms. In addition each of the examples given in connection with the various embodiments of the invention is intended to be illustrative and not restrictive. Further the figures are not necessarily to scale some features may be exaggerated to show details of particular components and any size material and similar details shown in the figures are of course intended to be illustrative and not restrictive . Therefore specific structural and functional details disclosed herein are not to be interpreted as limiting but merely as a representative basis for teaching one skilled in the art to variously employ the present invention.

As described herein various embodiments of the present invention relate to a pooled credit risk warehouse. In one example credit risk may be pooled e.g. by an entity a system a method and or a computer algorithm amongst all participants the entity may be subsequently delta neutral meaning that the entity has no exposure to the change in value or price of contracts offered .

In another example positions amongst participants may be held e.g. temporarily held in this pool whereby the reporting of account balances risk and profits and losses are managed e.g. by the entity the system the method and or the computer algorithm so that participants are ultimately assigned their positions vs. other participants within the predefined limits between participants in other examples other functions such as administrative and non administrative may be carried out e.g. by the entity the system the method and or the computer algorithm .

In another example participants may have two different accounts Margin and Collateral. These accounts may be employed entering positions whereby insufficient balances may prevent participants from posting orders or entering trades .

In one specific example Margin Accounts may be as follows Represent the cash or cash equivalent securities pledged to the pooled trade matching engine e.g. computer hardware and or software platform that dictates what positions a participant may purchase or sell. A concrete example which example is of course intended to be illustrative and not restrictive is as follows If the contractual obligation has a value of 5 000 in other words negative five thousand and a participant wants to sell 5 of these contracts that participant has to have 25 000 in other words positive twenty five thousand in their margin account to pay to the entity to ultimately be credited to the participant s who purchased these contractual obligations at a negative price. Similarly if a participant wants to purchase contracts that have a positive valuation they must have sufficient margin to purchase such contractual obligations.

In one specific example Collateral Accounts may be as follows Represent the cash or securities pledged to the pooled trade matching engine e.g. computer hardware and or software platform that dictates the total notional amount of the participants positions. A concrete example which example is of course intended to be illustrative and not restrictive is as follows Participant A wants to enter into 10 000 000 USD of contracts and there is a 10 collateral requirement for that type of contract traded for that type of participant the participant must have pledged 1 000 000 USD of cash or securities into the matching engine. In one example this helps mitigate marking to market moves.

In another example Accelerated Delivery may be triggered by 1 In the event that the entity e.g. the entity operating the pooled trade matching engine fails to perform its reporting or other duties 2 the failure of a participant to perform to its contractual obligations and or 3 if there is a material change to what the contract s value is based upon e.g. credit event of a reference obligation dissolution of a currency a successor event etc. typically all outlined in the contract .

In another example Accelerated Delivery may result in Participants are delivered their contracts at the contract rate defined by the last time participants accounts tied out. In one example this may be the previous business day or a longer period. In this example by having the contract value dictate the contract rate accelerated delivery has no economic effect on participants a true up .

In another example the present invention may utilize an investment bank broker broker dealer other financial institution and or Special Purpose Entity e.g. a Structured Investment Vehicle to intermediate these contracts e.g. for other non participant entities that wish to enter contracts .

In another example the present invention may utilize a CTFC SEC and or Foreign Equivalent registered clearing house to stand between participants until these participants no longer employ pooled credit in whole or in part for these contractual obligations between participants. In another example a CTFC SEC and or Foreign Equivalent registered clearing house may utilize an investment bank broker broker dealer other financial institution and or Special Purpose Entity e.g. Structured Investment Vehicle to enter into these contracts upon delivery vs. other participants e.g. for the purpose of clearing .

Reference will now be made to Tables 1 and 2 below. These tables provide an example which example is intended to be illustrative and not restrictive of credit extended between parties according to an embodiment of the present invention. Of note this table provides values at one point in time e.g. at an initial point in time as discussed herein the values will of course change as credit limits are changed parties enter and exit the pool etc. Of further note credit extended by a counterparty is listed down a column in Table 1 and credit received by a counterparty is listed across the rows of Table 1.

As seen from the above in this example in the event that two participants extend differing amounts of credit to each other the smaller number should control both parties may be informed of the discrepancy . In this case DIRECT v is only willing to extend 1 500 000 contract units of credit to DIRECT iv for this given transaction as opposed to the 2 000 000 contract units of credit DIRECT iv is willing to extend to DIRECT v .

Reference will now be made to an allocation procedure according to an embodiment of the present invention. In one example in order to facilitate the Allocation Procedure upon Accelerated Settlement all participants without regard to whether they maintained a position in an affected Reference Entity agree to accept assignment or assumption and release of Derivatives Position facing any other Participant in accordance with predefined Counterparty Exposure Limits with the sole provision that their delta remains unchanged through the delivery process e.g. as predefined and listed below . Allocation The pooled credit may continue to face counterparties step out of the trades or a combination of both or never having faced each other see e.g. the following tables and diagrams of .

In another example the present invention may provide a mechanism to permit parties the ability to trade in and out of a fungible product and at the same time keeping each trade bilateral.

In another example the present invention may provide a mechanism e.g. computer hardware and or software platform that tracks credit limits e.g. limits provided and amounts used .

In another example the present invention may provide a mechanism e.g. computer hardware and or software platform including an algorithm for optimal matching.

In another example the present invention may provide a mechanism e.g. computer hardware and or software platform that updates dynamically e.g. in real time or almost in real time .

In another example the present invention may provide a mechanism e.g. computer hardware and or software platform that checks to see if a sufficient amount of cash is available for a particular trade the checks may be performed for example at the order level and or at the trade level .

In another example the present invention may provide a mechanism e.g. computer hardware and or software platform that checks to see if a sufficient amount of collateral is available for a particular trade the checks may be performed for example at the order level and or at the trade level .

In another example the present invention may provide a mechanism e.g. computer hardware and or software platform that transfers funds e.g. after a trade .

In another example collateral may be tied to a particular contract as opposed to a particular counterparty.

In another example one party may pay a counterparty a difference in value related to a contract or position and the contract or position may then be re struck at a current rate.

In another example each bilateral agreement may be associated with at least one derivative or more contracts and types.

In another example each position or other obligation may have a value of x wherein the value of x is the same for each of the position or other obligations.

In another example each position or other obligation may have a value of x wherein the value of x can vary or differ between at least two of the position or other obligations.

In another example x may be weighted. In one specific example each x may be weighted the same. In another specific example at least one x may be weighted differently from at least one other x. In another specific example x may be weighted based on the underlying financial instrument e.g. emerging market note may count more towards a limit than a corporate note and or the parties involved and or other factors.

In another example a notional size of each position or other obligation may be the same for each position or other obligation.

In another example a notional size of one position or other obligation may vary or differ from a notional size of at least one other position or other obligation.

In another example a notional size of each position or other obligation may be weighted. In one specific example each notional size may be weighted the same. In another specific example at least one notional size may be weighted differently from at least one other notional size. In another specific example a notional size may be weighted based on the underlying financial instrument e.g. emerging market note may count more towards a limit than a corporate note and or the parties involved and or other factors.

In another example a mathematical algorithm may re allocate vectors between nodes to result in an optimal minimal credit usage amongst participants to maintain the same net position or market exposure.

In another example a mathematical algorithm may repeat various steps as a result of at least one of the following parties entering and or exiting entering and or exiting trades and or entering and or exiting participation in a credit pool mechanism changes in credit limits e.g. between and or among parties and or upon request for update including but not limited to end of day period reporting and or exposure reporting.

In another example the present invention may provide one or more of the following pooled credit bilateral arrangement first party and second party with no third party in between credit limits e.g. pre defined credit limits against individual limits of members of the pool so that each position never exceeds the defined bilateral limits maintain counter party credit through pooled credit and fungible product e.g. to minimize bilateral risk maintain the same derivative instrument while maintaining the same counter party risk limits eliminate or reduce the need for collateral due to the remedy of accelerated delivery deliver the underlying derivative at the option of the performing party.

In another example the present invention may in the event that approval of a trade is initially denied provide a mechanism to run through permutations to free up credit limits by reallocating usage amongst participants based on their pre defined limits.

In another example the present invention may check two credit limits for each position 1 that an individual credit limit does not exceed the aggregate credit limit of the pool for a particular party and 2 that the credit between any party does not exceed any of the limits afforded individually by any other party.

In another example the present invention may provide such as for example by running an algorithm on a computer for Maximum Matching E.g. utilize combinatorial optimization to reduce credit usage between individual participants in the pooled credit mechanism. This may be accomplished by reducing the number of intermediating nodes e.g. parties while adhering to individual credit limits resulting in an optimal minimal credit usage amongst participants to maintain the same net position or market exposure. This process may allow positions to be reallocated amongst participants providing that it doesn t change participants market exposure. This reallocation process may be done in a dynamic environment when participants are entering and exiting positions amongst each other.

In another example the present invention may provide such as for example by running an algorithm on a computer for Maximum Dispersion E.g. reduce lumpy exposures e.g. credit exposures that is diversify exposures e.g. credit exposures .

In another example the present invention may provide such as for example by running an algorithm on a computer for matching participants to maintain the net derivative position for each participant while minimizing the total size of positions between participants with the restriction that the matching results in no pair of participants having long or short positions with each other that exceed a bilateral credit limit between the pair of participants. The present invention may further provide for example for re allocating positions between participants to reflect this result resulting in an optimal minimal credit usage amongst participants to maintain the same net position or market exposure. The present invention may further provide for example for repeating these steps as a result of at least one of the following participants entering and exiting trades and or a pooled credit mechanism and or changes in credit limits and or upon request for update including but not limited to end of day period and exposure reporting. In one specific example this repeating may be done at set time intervals upon request and or at the introduction of every new trade. In another example the restriction may be based upon and or reflect previous trading activity between parties.

In another example the present invention may provide for a combination of types of positions against one credit limit e.g. a first derivative type and a second derivative type against a single credit limit.

In another example the present invention may provide for a combination of types of positions against a plurality of credit limits e.g. a first derivative type against one credit limit and a second derivative type against another credit limit.

In another example if approval of a requested trade is not initially made one or more of the following steps may be carried out reallocating at least part of at least one position between at least one of the one through n parties other than a first one of the one through n parties to the first one of the one through n parties calculating with the computer system an updated value of remaining available credit by subtracting a value of the requested use of credit by the first of the one through n parties from a previously calculated available credit for the first of the one through n parties plus the reallocated position approving the requested trade with the computer system if the value of the calculated updated remaining available credit associated with the first of the one through n parties is greater than or equal to zero and settling the requested trade if the requested trade has been approved.

Reference will now be made to various examples related to the Application of Combinatorial Optimization Dynamic Programming and Graph Theory to Pooled Credit including for example Allocation Algorithms and or or Maximum Matching and or Dispersion within Pooled Credit . Of course this discussion is provided as an example only and is not intended to be restrictive.

In the section below we explain how a system that consists of Derivatives contracts a group of parties trading these contracts and certain credit limits placed by the parties on each other can be depicted using constructs from the Graph Theory. Following this we show how this graph based representation can be used to make optimizations in such a system.

The credit exposure of parties involved in the Derivatives Trade for a particular contract can be depicted by a Directed Graph G V E where the vertices V represent the parties trading that Derivatives contract and the each edge e E represent a credit position.

The total outstanding credit in the system is the sum of the weights of all the edges of G V E or T Total Credit w e .

We will call this limit the credit limit. The credit limit extended by party u to v is given by function c u v and can be depicted by a matrix structure as in .

It can be seen from the credit limit matrix in Table 3 below that the credit extended from party A to B is 10 or c A B 10 and that parties A and C have no limits extended to each other or c A C c C A 0.

At any time parties may trade more than one contract on the system. For example party A may trade a 5 year contract on IBM and a 5 year contract on Ford as well as a 3 year contract on IBM. For each contract C Cthrough C there will be corresponding Graphs G V E G2 V E through G V E . It is critical that there exist a separate graph for each contract to be able to make optimizations.

Hence the system can be completely represented by the set of graphs and the credit limit matrix. Mathematically the system consists of 

read as for each tuple such that u v are elements of the party set P the sum of the weights of all edges across all graphs in G must be less than the credit limit in matrix C for .

We define Net Position of a vertex as the sum of the weights of all edges inbound to that vertex minus the sum of the weights of all edges outbound from that vertex. From the net position of vertex D is 5 weight of incoming edge AD 3 outgoing edge DC 2.

The optimizations made in the system must ensure that the net value of the credit positions of the parties does not change. Hence the net position of every vertex must be preserved.

Given the goal of minimizing the credit exposure while respecting the given constraints the problem can be considered as a Path Minimization problem. As in to get from a. to b. for the graph for Instrument 1 the path was minimized to as vertex B was eliminated. We can define collapsing of edges as a basic operation in such a minimization as follows 

Collapsing is the process of Transforming a graph G V E with weight function W by reallocating its edges of into a new Graph G V E where V V with weight function W such that W E W E that is the sum of weights of the edges of a new graph is less than the sum of weights of the edges of the old graph AND the net position of each vertex in V is preserved.

Given two adjacent edges e1 u v and e2 v w of a directed graph G V E such that u v w V and e1 e2 E collapsing can be performed by creating a new edge e3 u w such that w e3 min w e1 w e2 and changing the weights of the e1 and e2 to be w e1 w e1 w e3 and w e2 w e2 w e3 respectively.

Using the collapsing approach towards minimization the solution can be considered to be a series of decisions. At any point while optimizing the system there will be tuples of adjacent edges available from the various graphs in the system to collapse. Hence at any stage of optimization there will be 2 kinds of decisions to be made 

Given that at any time in the system there may be a number of different graphs the number of possible decisions becomes the sum of all possible collapse configurations at all possible vertices of each of these graphs.

Such a combinatorial explosion indicates the applicability of combinatorial optimizations in the solution. The first such solution we discuss is that using the principles of Dynamic Programming.

Consider a system of 3 instruments with 4 parties A B C D that have extended a credit limit of 10 to each other that is for each edge e in each graph G of the system c e 10 with initial state as in Step 1 of . The sum of the weights of all edges of all graphs for this system is 40.

In Step 2 if we choose to collapse a path from Instrument 2 we have 2 choices at vertex C. We could collapse path or . Note that there are 2 choices available on vertex 2 as the number of incoming edges is 2 and outgoing edges is 1 and 2 1 2. The decision in is to collapse resulting in the system state of Step 3.

In Step 3 we notice that there are no more paths that can be collapsed for Instrument 2. For Instrument 1 is the only candidate for collapsing and for Instrument 3 is the only one. Step 4 shows the system state after collapsing and .

At this point there are no more paths that can be collapsed in the system. The sum of the weights of all edges of all graphs of the system comes out to be 22 which is less that what we started with 40 and yet the net position of each vertex in each graph is preserved.

In this section we present example pseudo code for an algorithm that uses dynamic programming to optimize the system.

20 Let subg be the set of all possible graphs that will be the result of a collapse operation on vertex v

The algorithm presented in Listing 1 will result in a decision tree via recursion. The base criteria of the recursion occurs when no more collapsing can be done on any of the graphs. The procedure Value calls itself recursively to generate a decision tree. The depth of the decision tree will depend on how soon the minimum graphs that cannot be collapsed further are obtained. The breadth of the decision tree depends on how many subgraphs are obtained from the split operation on each level.

The procedure checkFeasibility on Line 4 will check each generated subgraph for its feasibility. If a subgraph has characteristics that prove it to be sub optimal or infeasible it will be eliminated from further consideration hence decreasing the breadth of the recursion .

In addition to the collapsing approach to optimization we present an approach that calculates the Net Position of each party or vertex in each graph to start with and creates corresponding new graphs from scratch with parties vertices having the same net positions as in the previous graphs.

This approach indicates the problem to be one of maximum matching or distribution of net positions so as to obtain a minimum of open interest or sum of the weights of the edges of each graph in the overall system.

It is possible to apply dynamic programming to solve the above problem as well. Consider the 2 Instrument system of .

At any step there is a choice of allocating lto n units depending on the credit limit matrix from A D E in Instrument 1 to B or C in Instrument 1.

Similarly there is also a choice of allocating 1 to n units from A B C in Instrument 2 to D E in Instrument 2.

An algorithm similar to that in Listing 1 can be applied to such a decision based approach as well. It may be noted that this problem is reminiscent of the classic Knapsack Problem albeit with additional constraints and modifications.

It is possible to have 2 systems with parties having the same net positions but different credit exposures to each other. We present an example in .

The 2 systems in the above figure are equivalent in terms of their net positions but system configuration b. allows a wider distribution of credit exposure among parties. In other words in configuration a. party B has an exposure of 2 versus party A while in configuration b. party B has an exposure of 1 versus C and 1 versus A hence maintaining a net position of 2 but having the credit exposure distributed over parties hence reducing credit risk.

Once we have obtained a system that optimizes open interest by reducing it to a minimum we will next redistribute the credit risk among parties while maintaining the open interest as well as the Net Positions.

Parallelization may be used to evaluate the different paths that are generated by the dynamic programming algorithms in order to speed up the computation.

For the purposes of this disclosure a computer readable medium is a medium that stores computer data in machine readable form. By way of example and not limitation a computer readable medium can comprise computer storage media as well as communication media methods or signals. Computer storage media includes volatile and non volatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Computer storage media includes but is not limited to RAM ROM EPROM EEPROM flash memory or other solid state memory technology CD ROM DVD or other optical storage cassettes tape disk or other magnetic storage devices or any other medium which can be used to tangibly store the desired information and which can be accessed by the computer.

Further the present invention may of course be implemented using any appropriate computer readable medium computer hardware and or computer software. In this regard those of ordinary skill in the art are well versed in the type of computer hardware that may be used e.g. a mainframe a mini computer a personal computer PC a network e.g. an intranet and or the Internet the type of computer programming techniques that may be used e.g. object oriented programming and the type of computer programming languages that may be used e.g. C Basic . The aforementioned examples are of course illustrative and not restrictive.

While a number of embodiments of the present invention have been described it is understood that these embodiments are illustrative only and not restrictive and that many modifications may become apparent to those of ordinary skill in the art. For example certain methods may be computer implementable or computer implemented. In this regard it is noted that while such methods can be implemented using a computer the methods do not necessarily have to be implemented using a computer. Also to the extent that such methods are implemented using a computer not every step must necessarily be implemented using a computer. Further any steps described herein may be carried out in any desired order and any steps may be added and or deleted .

