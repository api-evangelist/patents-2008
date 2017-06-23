---

title: Method for solving combinatoral optimization problems
abstract: A method for solving a combinatorial optimization problem and applying the solutions to routing as employed in naval convoying and other transit point scheduling. The method involves isolating a plurality of vertices into open-ended zones with lengthwise boundaries. In each zone, a minimum length Hamiltonian path is found for each combination of boundary vertices, leading to an approximation for the minimum-length Hamiltonian Cycle. The method discloses that when the boundaries create zones with boundary vertices confined to the adjacent zones, the sets of candidate HPs are found by advancing one zone at a time, considering only the vertices in the zone in question (with embedded HPs from previous zones) and an adjacent zone in the direction of progression. Determination of the optimal Hamiltonin paths for subsequent zones has the effect of filtering out non-optimal Hamiltonian paths from earlier zones.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08073797&OS=08073797&RS=08073797
owner: The United States of America as represented by the Secretary of the Navy
number: 08073797
owner_city: Washington
owner_country: US
publication_date: 20080929
---
The invention described herein may be manufactured and used by or for the Government of the United States of America for governmental purposes without the payment of any royalties thereon or therefor.

The present invention relates to a method for solving optimization problems particularly minimal Hamiltonian cycle type problems and a practical utilization of the solutions for these problems including the application of the solutions to routing as employed in naval convoying or other transit point scheduling.

It is known in the art that a Traveling Salesman Problem TSP involves finding a minimum length Hamiltonian Cycle HC the path of visiting each vertex once and returning to the starting vertex. The minimum length HC resolves the routing problem of the TSP which can also be applied to naval convoying trucks routes or even transit point scheduling such satellite positioning.

The symmetric TSP with N vertices has N 1 2 permutations precluding an exhaustive search except for small N. Even a relatively small problem e.g. N 20 has 10distinct HCs N 40 leads to 10distinct HCs. The Euclidean TSP is classified as an NP hard problem having no known algorithm for the general case whose number of operations is a polynomial function of N.

The N 1 2 permutations assume that any vertex can occupy any of N positions. Isolating vertices into spatial zones locks each into a limited range of positions subject to boundary vertex permutations. This falls into a general area of dynamic programming.

Partitioning the vertices into sub problems has been done for the Euclidean TSP. In particular a Polynomial Time Approximation Scheme PTAS generates a tour exceeding the optimal length by no more than a factor of 1 in time N. The approach involves a bounding square box dissected into squares and shifted randomly with restrictions on edge crossings to specified portals .

Most prior work on the TSP has focused on heuristics that generate tours. For example a simple heuristic involves going to the nearest point. More complex heuristics include genetic algorithms simulated annealing and neural nets. In some cases these approaches have found optimal tours. More likely the approaches will come close often to within two percent of the optimal tour.

Another approach to the TSP makes use of a DNA Computer . This approach involves DNA strands with appropriate genetic coding to represent each point mixed together in a test tube. A 7 point problem was solved by chemically eliminating all non solutions. Although this process avoids exhausting every possible permutation creating during the chemical reactions the process may take several days to find a solution.

Practical applications connected with the TSP go beyond traditional combinatorial problems involving scheduling and routing e.g. planning of supply convoy routes to support naval bases . In physics a three dimensional Ising model used for studying phase transitions can be translated into a TSP problem. Scattering of X rays from crystals can potentially involve accounting for as many as 30 000 different radiation paths. Other applications include VLSI chip fabrication protein structure prediction and the assignment of frequencies to transmitters in a communications network. Existing patent references disclose methods for solving the TSP 

In Marks et al. U.S. Pat. No. 6 826 549 a system is provided that enables an interactively guided heuristic search for solving a combinatorial optimization problem. The system initially performs a hill climbing search of the combinatorial optimization problem to obtain a solution using initial default parameters. The current solution and the combinatorial optimization problem are visualized on an optimization table a table top display device. The parameters are altered based on the visualization of the combinatorial optimization problem and the current solution. Then the searching visualizing and setting are repeated until the solution is selected as an acceptable solution of the combinatorial optimization problem. During the repeating the parameters can be a set of probabilities and in which case the search is a random perturbation based search. Alternatively the parameters can be a set of priorities in which case the search is an exhaustive local search.

In Okano U.S. Pat. No. 6 510 384 a method is provided for increasing the execution speed of a cost minimizing routing algorithm as employed in trucking or job shop scheduling. Penalty functions for succeeding transit points along a route are added and examined for validity during trial route evaluation. A soft time window is set for each transit point and proposed routes are evaluated using a total cost including all soft time windows along the route and the length of the route. A static soft time window function and a dynamic soft time window function are correlated with each transit point. The dynamic soft time window function for each transit point is the sum of the static soft time window function for the transit point and the dynamic soft time window function for a succeeding transit point in the direction of travel.

In Goray et. Al. U.S. Pat. No. 6 636 840 a computer system and associated method is configured to support solving NP complete problems such as minimal Hamiltonian cycle type problems. A primary network represented by the matrix of its edges is recorded in the memory space and an equivalent representation of the primary network is formed as a set of subnetworks. Nodes of a present path are reordered according to a set of reordering rules and edge weights of edges of the set of subnetworks are changed according to a set of edge weight changing rules.

It is therefore a general purpose and primary object of the present invention to provide a method for solving a combinatorial optimization problem that can include the Traveling Salesman Problem .

It is a further purpose of the present invention to provide a method for solving a combinatorial optimization problem of naval conveying or other transit point routing scheduling.

The approach in the present invention dissects a set of vertices lengthwise. A line can dissect vertices contained in a plane while a plane can dissect vertices disturbed in a three dimensional space. The approach then finds optimal Hamiltonian Paths HPs paths by visiting each vertex once for the isolated zones independently of the other zones.

The number of combinations of boundary vertices i.e. vertices that can extend edges from a zone to the adjacent zone determines the number of optimal HPs for each zone. Sets of optimal HPs for each zone with embedded HPs from previous zones generate an HC for the set of vertices.

The present invention illustrates the procedure for a benchmark problem small enough to permit a detailed description of the entire solution process. For example the ATT48 benchmark problem known to those skilled in the art and to those who would try to resolve a combinatorial optimization problem.

The success of the approach depends on limiting the number of potential boundary vertices and crossing edges. In practice sometimes as few as two edges will cross a boundary from one zone to another. The number of crossing edges can be increased to improve the solution. For example if the optimal HC has four crossing edges between zones the solution will improve by increasing the number of crossing edges from two to four.

In the present invention the TSP problem is broken down into subproblems that depend on each other through boundary interactions. The boundaries separate zones and have a lengthwise nature. The boundaries form open ended zones.

A single lengthwise boundary cuts the optimal HC into an even number of HPs the sum of which must have the minimum length in each of the two created spatial zones. For example if two HPs are created the HP in each created zone terminated at boundary vertices in the other zone must have the minimum length. If an HP length exceeds the minimum replacing the length with another HP having the same vertices will reduce the overall HC length. Stated another way it is not possible to dissect the optimal HC into two HPs and replace one of them with a shorter HP having the same vertices. Each HP from the optimal HC will be the shortest length for that set of vertices.

The boundary vertices contained by the optimal HC associated with a particular dissection are not generally known therefore enumeration is required of all possible boundary vertices located in the adjacent zone. Typically not all potential boundary vertices will connect edges to the adjacent zone. For example as few as two edges n 2 could connect two zones. For each value of n the binomial coefficient

The second boundary isolates both zones 1 and 2 from the other vertices. The approach then finds the set of minimum length HPs for the combined vertices zones 1 and 2 except that the previously determined HPs from zone 1 become embedded in the new HPs.

Boundary vertices can comprise all the vertices in the adjacent zone or more likely a smaller subset. Boundary vertices are usually those vertices closest to the boundary. Vertices close to the boundary often have the effect of eliminating other potential boundary vertices because the latter often lead to non optimal HCs. Table 1 lists the zones and boundary vertices that will be depicted in thru . Vertices 5 33 18 7 19 37 are not boundary vertices as they are shielded by other vertices closer to the boundary which is why they are not considered.

The set of minimum length HPs found for each zone combined with all previously considered zones includes embedded HPs from the previous zones. Embedded HPS are those in which the solution has already been determined. However as the approach determines HPs for later zones the approach filters out non optimal embedded HPs from previous zones until at the last zone n b 2 and no extraneous HPs remain.

The method of the present invention discloses that when the introduced boundaries create zones with boundary vertices confined to the adjacent zones the sets of candidate HPs are found by advancing one zone at a time whether on a two dimensional plane or across a three dimensional space considering only the vertices in the zone in question with embedded HPs from previous zones and an adjacent zone to the right or in the direction of progression.

In the vertices of a typical transit point scheduling separate ten zones by means of nine introduced boundaries each dissecting as a lengthwise illustration. As shown in succeeding figures thru each zone is connectable to adjacent zones via a limited number of edges. An edge is a straight line connecting two vertices.

The Zone 1 vertices 4 35 and 45 can connect to two of the three boundary vertices in Zone 2 via inter zone edges according to one of three combinations 10 and 26 26 and 24 or and 24. Determination of minimum length HPs involves evaluating all interior vertex permutations for each of the three boundary vertex combinations. Table 2 shows the results.

As shown in introduction of the second boundary between Zone 2 and Zone 3 leads to the determination of HPs for the combined vertices in Zone 1 and Zone 2 vertices 26 10 and 24 . Each HP could terminate to two or more of the boundary vertices 2 29 42 48 39 and 32 in Zone 3. Vertex 5 is not considered a boundary vertex because vertex 2 is directly in front of vertex 5 thereby making it unlikely that vertex 5 would extend into zone 2.

When n 2 the six boundary vertices in Zone 3 have fifteen possible combinations. Although n 4 is possible it would require two edges from vertex 10 to cross the boundary. Including extra crossing edges would lead to the evaluation of more boundary vertex combinations and would involve determining optimal HPs on the basis of the sum of their lengths with embedded HPs from Zone 1 . Minimizing n when possible reduces computation time.

Table 3 shows the possibilities searched in Zone 2 for the candidate HPs when n 2. Vertices Vand Vare two of the boundary vertices 2 29 42 48 39 and 32. Embedded HPs 10 24 10 26 and 24 26 are shown in bold typeface both in the text and the tables that follow.

Each of the twelve possibilities in Table 3 are searched for the fifteen V Vcombinations to obtain fifteen minimum length HPs for Zone 2 Table 4 with embedded HPs in bold typeface. The Zone 2 solution contains only embedded HPs 26 10 and 26 24 eliminating HP 10 24 See .

The Zone 3 solution Table 5 has only two distinct embedded HPs 2 42 and 32 42. HP 32 42 is not the minimum length HP but HP 32 42 will not be eliminated until later. All other HPs were eliminated in the Zone 3 solution. Embedded HPs in Table 5 are indicated in bold. Table 4 shows that both HP 2 42 and HP 32 42 contain the embedded HP 26 10 from Zone 2.

Zone 4 connects edges to four boundary vertices in Zone 5 Table 6 generating two HPs for each boundary vertex combination. For each case either 1and 2and 3and 4 or the 1and 4and 2and 3boundary vertices can define the two HPs effectively doubling the number of combinations. The number of vertices in each HP can vary but must sum to ten and only the pair that minimizes the sum of their lengths is retained.

Zone 4 contains only six distinct embedded HPs 34 21 34 25 25 21 41 21 and 41 25. Edges 32 21 and 29 34 are both contained by embedded HP 34 21.

Zone 5 Table 7 has only four distinct sets of embedded HPs from Zone 4 16 23 and 47 11 16 47 and 3 23 16 47 and 23 11 16 23 and 11 47.

Table 6 shows that the four distinct HPs in Zone 4 that are embedded in Zone 5 contain only two distinct HPs from Zone 3 34 21 and 41 21. Both have the embedded HP 2 42. In HP 2 42 is contained in HP 34 21 shown . HP 41 21 is not shown but differs only in that edge 41 29 replaces edge 34 29 so both contain HP 2 42. In other words the approach continues to automatically filter out extraneous HPs that locally had a minimum length in a previous combination of zones for a particular boundary vertex combination but are not consistent with the global minimum length HC.

In Table 7 the first HP connects two edges to Zone 6. The second HP demonstrates the closing the loop process necessary when the number of crossing edges n decreases from one boundary to the next. In this case n decreases from four across the fourth boundary to two across the fifth boundary and both ends of the 2HP terminate at boundary vertices in Zone 4. The loop closes when the HP crosses back into to capture vertex 13 25 and 14. As already noted the terminating loop can contain ends from two separate HPs from Zone 4. For example the HPs 16 47 and 11 23 from Zone 5 lead to HPs 20 12 in Zone 6 HP 16 23 terminates in Zone 5 when n 2 in Zone 6. In other words HP 11 23 and vertices 3 22 and 16 coalesce into HP 16 11 which terminates in Zone 5.

Zones 6 to 8 have only two edges connecting to either adjacent zone. The only remaining embedded HPs in Zone 6 Table 8 are 12 20 and 1 20 reducing the embedded HPs from Zone 5 to 11 47 and 16 23 16 47 and 23 11.

Table 9 indicates that Zone 7 has only one embedded HP 38 46 which has the effect of eliminating all extraneous non optimal embedded HPs from all previous zones.

Finally both Zones 8 and 9 have only two edges crossing their right boundaries n b 2 reducing the number of minimum length HPs in both cases to one 27 19 37 6 28 30 43 Zone 8 and 17 27 43 17 Zone 9 .

The optimal HC Table 10 results from working backwards to extract the embedded HP 28 30 from the Zone 8 solution and then extracting the embedded HP 38 46 from the Zone 7 solution etc. Substituting all of the vertices into embedded HPs leads to the overall solution. In the vertices of the embedded HPs are circled.

Introducing lengthwise boundaries allows optimal HPs to be determined locally for each zone one for each boundary vertex combination . The lengthwise boundaries also allow the solution to progress successively from zone to zone automatically filtering out previous HPs that are inconsistent with a globally minimum length HC. Embedded HPs from previous zones helps to reduce the computation time.

The solution efficiency depends on the number of boundary vertices and crossing edges for each zone. The referenced ATT48 problem requires only two interzone edges from each zone except Zone 4 which has four inter zone edges to Zone 5 . Although the approach considered only limited values of n and b rather than all possible values the approach can also increase n and b for more complex problems.

Including results for n 2 or n 4 for Zone 4 will add non optimal solutions to ATT48 increasing the computation time linearly with the added number of combinations.

The foregoing description of the preferred embodiments of the invention has been presented for purposes of illustration and description only. It is not intended to be exhaustive nor to limit the invention to the precise form disclosed and obviously many modifications and variations are possible in light of the above teaching. Such modifications and variations that may be apparent to a person skilled in the art are intended to be included within the scope of this invention as defined by the accompanying claims.

