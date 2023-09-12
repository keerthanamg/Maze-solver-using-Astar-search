# Maze-solver-using-Astar-search
Design and analysis of Algorithms Lab mini project:

-> ABSTRACT:
A-Star (A*)search algorithm is an intelligent algorithm to solve a graph problem. Contrary to Depth First Search (DFS) and Breadth First Search (BFS), A* is an informed search algorithm which means that it takes into account the position/location of the goal while searching for it and hence it searches quite a few nodes to reach the goal. We have developed the A* algorithm in Python to solve the Maze Problem.We have used frontend languages like Javascript, Html and CSS for the web page.

1.INTRODUCTION:
A * algorithm is a searching algorithm that searches for the shortest path between the initial and the final state. It is used in various applications, such as maps.
In maps the A* algorithm is used to calculate the shortest distance between the source (initial state) and the destination (final state). Here we have used the A star search to find a path in the maze.
A* algorithm has 3 parameters:
g : the cost of moving from the initial cell to the current cell. Basically, it is the sum of all the cells that have been visited since leaving the first cell.
h : also known as the heuristic value, it is the estimated cost of moving from the current cell to the final cell. The actual cost cannot be calculated until the final cell is reached. Hence, h is the estimated cost. We must make sure that there is never an overestimation   of the cost.
f : it is the sum of g and h. So, f = g + h

2.PROBLEM STATEMENT:
We create a maze with starting and end points with barriers , find the path from the start point to the end point:
Determine if there is a path from the start point to the endpoint.
Specify your path without using circles or loops.
Avoid barriers if any are faced.

3.LITERATURE REVIEW:

[1] A* is a search algorithm that has long been used in the pathfinding research community. Its efficiency, simplicity, and modularity are often highlighted as its strengths compared to other tools. Due to its ubiquity and widespread usage, A* has become a common option for researchers attempting to solve pathfinding problems. However, the sheer amount of research done on the topic makes it difficult to know where to start looking. With this paper, we hope to create an accessible, up to date reference on the current state of the A* search algorithm for future pathfinding projects to consider. This paper examines A-Star’s current usage in the field of pathfinding, comparing A* to other search algorithms. It also analyzes potential future developments for A-Star’s development. A* cannot keep up with the demands of current pathfinding problems. Other algorithms can maintain the same performance while also demanding less overhead and this problem only grows worse as grid size increases. However, use of innovative modifications such as different heuristic types or secondary components to the algorithm allow A* to achieve very fast times with good accuracy when dealing with large maps, while only having slightly increased overhead costs for the modifications. While beginning to show its age, improved algorithms based on the classic A* algorithm are more than capable of keeping up with modern pathfinding demands. These derivative search algorithms such as HPA* is used to overcome the limitations of A*. HPA* can compete with and even surpass its competitors depending on the challenge faced.

[2]Path planning plays an essential role in mobile robot navigation, and the A* algorithm is one of the best-known path planning algorithms. However, the traditional A* algorithm has some limitations, such as slow planning speed, close to obstacles. In this paper, we propose an improved A*-based algorithm, called the EBS-A* algorithm, that introduces expansion distance, bidirectional search, and smoothing into path planning. The expansion distance means keeping an extra space from obstacles to improve path reliability by avoiding collisions.algorithm, the proposed algorithm improves the path planning efficiency by 278% and reduces the number of critical nodes by 91.89% and the number of right-angle turns by 100%.

[3]The A* optimization methods introduced above only incompletely optimize the efficiency of the algorithm and still present defects, which means that the efficiency of the algorithm.Bidirectional search is a strategy searching path from the start node and the goal node simultaneously. Smoothing improves path robustness by reducing the number of right-angle turns. In addition, simulation tests for the EBS-A* algorithm are performed, and the effectiveness of the proposed algorithm is verified by transferring it to a robot operating system (ROS). The experimental results show that compared with the traditional A* 
can still be more thoroughly optimized. None of the above algorithms consider optimizing the robustness of the algorithm. Therefore, the improvements and variants of the A* algorithm remains flawed.

[4]A* (a-star) is a well known best-first search algorithm that has been applied to the solution of different problems. In recent years, several extensions have been proposed to adapt it and improve its performance in different application scenarios. In this paper, we present a survey and classification of the main extensions to the A* algorithms that have been proposed in the literature. We organize them into five classes according to their objectives and characteristics: incremental, memory-concerned, parallel, anytime, and real-time. For each class, we discuss its main characteristics and applications and present the most representative algorithms.

<img width="700" alt="Screenshot 2023-09-12 at 7 44 03 PM" src="https://github.com/keerthanamg/Maze-solver-using-Astar-search/assets/88154987/4f39d1c8-d641-42c6-ba92-ab299b8fbc1a">
<img width="700" alt="Screenshot 2023-09-12 at 7 51 35 PM" src="https://github.com/keerthanamg/Maze-solver-using-Astar-search/assets/88154987/312f9432-314f-457c-94d4-c87867dd0748">
<img width="700" alt="Screenshot 2023-09-12 at 7 52 42 PM" src="https://github.com/keerthanamg/Maze-solver-using-Astar-search/assets/88154987/da47dd5f-f806-4af1-aa9e-285be95c65cc">

4.REQUIREMENTS:
> HARDWARE REQUIREMENTS:
PC

> SOFTWARE REQUIREMENTS:
PYTHON
FAST API
MIDDLEWARE
JAVASCRIPT
REACTJs
NPM NODE MODULES

5.DESIGN
5.1. METHODOLOGY

A* algorithm is very useful in graph traversals as well. 
Suppose  you   have  the   graph  and  you  apply A* algorithm on it. The initial node is A and the goal node is E.  We do not  know the cost to reach the goal cell  so we will  simply estimate  that.  There can  be two functions to estimate that. 
One of the keys of the A* search algorithm compared to other search or pathfinder algorithm  compared  to  other  search  or  pathfinder algorithms is the use of some heuristic function to determine or estimate the current cost from the start point and the  future  cost  to  the  end  position  or  goal.  Based  on  this cost calculation the algorithm  will  explore  the  different  paths and choose the one that minimizes the cost to the goal.  The  most basic cost can be easily calculated as the distance to the goal.
For example positions farthest to the goal point will be more costly than the closest ones, however different terrains will also be more costly than others, for example mud over a paved road. We could also create a cost function for the altitude or slope in the terrain. Finally, some obstacles may be impassable and they will affect the final path. 
The first data structure we will use in the A* search algorithm implementation will be a simple node list. This node list will represent a path to the goal position. We will be building node by node as we discover better ways to navigate around obstacles while minimizing the accumulated cost of the routeOne node represents a position in the map with accumulated cost, and it will reference a parent node it is connected to. Traversing the nodes in reverse from the last child to the first parent will produce a route from the starting point to the last node in the list. 

As you can see the PositionNode class have 3 properties: 
 reaching the goal point we can return the last connected node and we need to reconstruct a path of points cost related to the accumulated cost from the start of the route. 
position as a tuple, or two position array with x and y.
parent as the reference to the parent node object who is another object of the PositionNode class. An object with a null or None value in parent would be the root node or the starting position in the path.

Running the main search algorithm loop will look like this:
1. Check if any node in the list to visit have a lower cost. If so, select it as the current node.
2. Move the current node from the “nodes to visit” list to the “visited nodes”list
3. Check if the current node is actually the goal position by checking the position coordinates. If so we are done! and we will return the last linked node that should be the goal position node.
4. Check all possible movements from the current node and create their nodes, updating the current cost for all of them
5. Add new nodes to nodes to visit list ONLY if the same position is not in the list OR its accumulated cost is lower than the previously added node for the same position. This is important to note, because we may visit the same position more than one time but as part of a different route with a lower accumulated cost.
If we run out of nodes to visit during our main search loop, no path can be found in the map, probably because the start position to the goal position is disconnected or blocked by some impassable obstacle like walls. After successfully by just traversing the nodes in reverse using the referenced parent until the last node with a null or None parent. Reversing this list of points will give us the correct order from start to finish position.

HTML (the Hypertext Markup Language) and CSS (Cascading Style Sheets) are two of the core technologies for building Web pages. HTML provides the structure of the page, and CSS the (visual and aural) layout. Javascript is used by programmers across the world to create dynamic and interactive web content like applications and browsers. JavaScript is so that it's the most used programming language in the world, used as a client-side programming language by 97.0% of all websites.
For frontend we use these languages.We incorporate this interface with the A* search algorithm..For A* search algorithm implementation we use python which acts as a backend.


5.2.MODULE:


<img width="700" alt="Screenshot 2023-09-12 at 8 01 13 PM" src="https://github.com/keerthanamg/Maze-solver-using-Astar-search/assets/88154987/86e1feac-d264-49d0-82bc-da949b1d79cf">


6. OUTPUT SCREENSHOTS:
<img width="700" alt="Screenshot 2023-09-12 at 8 10 28 PM" src="https://github.com/keerthanamg/Maze-solver-using-Astar-search/assets/88154987/f6170aa2-16d2-4e03-8fca-54ba04502800">
<img width="700" alt="Screenshot 2023-09-12 at 8 12 41 PM" src="https://github.com/keerthanamg/Maze-solver-using-Astar-search/assets/88154987/71d7d9e6-dacb-44d3-bc8f-d8f671120c93">
<img width="700" alt="Screenshot 2023-09-12 at 8 13 24 PM" src="https://github.com/keerthanamg/Maze-solver-using-Astar-search/assets/88154987/c4bf76ec-90f1-42be-a418-a9cd47bf7eab">

7. CONCLUSION:
If we run out of nodes to visit during our main search loop means that no path can be found in the map, probably because the start position to the goal position is disconnected or blocked by some impassable obstacle like walls.
After successfully reaching the goal point we can return the last connected node and we need to reconstruct a path of points by just traversing the nodes in reverse using the referenced parent until the last node with a null or None parent. Reversing this list of points will give us the correct order from start to finish position.

8. REFERENCES:
[1]  Felner A, Li J, Boyarski E, Ma H, Cohen L, Kumar T et al. Adding Heuristics to Conflict-Based Search for Multi-Agent Path Finding. International Conference on Automated Planning and Scheduling. 2018.

[2]  Hart PE, Nilsson NJ, Raphael B. A formal basis for the heuristic determination of minimum cost paths. IEEE transactions on Systems Science and Cybernetics. 1968;4(2):100–107.

[3]Tang G, Tang C, Claramunt C, Hu X, Zhou P. Geometric A-Star Algorithm: An Improved A-Star Algorithm for AGV Path Planning in a Port Environment. IEEE Access. 2021;9:59196–59210.

[4] Song R, Liu Y, Bucknall R. Smoothed A* algorithm for practical unmanned surface vehicle path planning. Applied Ocean Research. 2019;83:9–20.

