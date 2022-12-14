# Street-Mapper
* Name: Mustafa Mudassaar
 * NetID: Mmustafa
 * Email: mustafamudassar_2024@depauw.edu
 * Assignment: Project 3
 * Lab: TR 4:50pm-6:05pm.

 * Lab Partner:
 * Name: Murtaza Hassan
 * NetID: Mhassan
 * Email:  murtazahassan_2024@depauw.edu

Files:
Node.java, Edge.java, Graph.java, Canvas.java, StreetMap.java, map.png, map2.png. The two png files are just icons we add into our map at the starting node and ending node. The node file represents an intersection, the edge file reprsents a node and is also used to calculate weights of the edges. The graph file implements the shortest path calculation. The Canvas file is used to draw the map, handling the JFrame part of our project. The StreetMap class is the class with the main method, and uses inputs from cmd to give output of our project. 
Starting off, we first defined the basic classes: Node, Edge and Graph. Then we both handled the construction of the graph from the input file that is provided to us. The implementation of Dijkstra's algorithm was also handled by the both of us to find the shortest path between two points provided by the user if their exists a path between them. The calculation of distance in miles of this path and printing of path was done by Murtaza. Mustafa worked on the Canvas class which involves the drawing and scaling of the map, and drawing of the the shortest path using the path that was computed and Murtaza created the main-class to use command line arguments for input and to call other classes properly to draw map and path. We both worked on the extra credit parts together, working on ideas and determining how to add its code.

The general working for the code is that it takes an input txt file, creates a graph consisting of Nodes and Edges. Each graph has a hashmap of nodes called vertices and each node has a hashmap of edges for it's neighbours which makes up the adjacency list. After we created the graph, it calculates the shortestpath using the method that we created for the Dijkstra algorithm. It also renders the graph on the JFrame which depends on the input provided by the user. We decided to explain the whole process of calculation of this shortest distance and drawing in more detail below.
It takes about O(|E|) to O(|V|^2) to draw map. The working of the algorithm is that for every node in the graph's hashmap of vertices which is O(|V|), we calculated the x and y coordinates using the latitude and longitude degrees. For every node in it's adjacency list, we found the x,y coordinates and drew a line connecting that node with it's neighbour. To draw the shortest path some modifications were done by us: when we implemented Dijkstra we used a stack to push the updater/parent nodes to and then we popped the updater/parent nodes from the stack to find and return the shortest path. While drawing the map we used a thick red line to draw the shortest path and we added some graphic elements such as location pointers and we made a JPanel on the South side which prints out the starting, ending locations and the distance. We also implemented a find tab where you can insert the starting and ending point and it will find the new path for you again. On the North Panel we implemented a button which changes the background color of the frame and we named it as a day and nightmode for the map.

Shortest Path: the worst case runtime of shortest path algortihm is V^2log(V) because we extract the minimum from the priority queue, at most V times. We check all adjacent nodes of the current node add them to priority queue accordingly. Finally when we have all the shortest path we use the updater node of each node to put all those updater nodes onto a stack after which we pop those nodes from the stack to get the shortest path.

Obstacles/ design hurdles:
-Starting the project we did not understand that an intersection meant Node, and road meant Edge, immediately. This took some rereading of the handout, input files and visualizng how our code should run by drawing out what it will do on paper. 

-For the dijkstra's algorithm we first made a very inefficient method as we added all the nodes initially to the priority queue but both of us realized that and then we designed a method which took only the starting Node and explored that and added the nodes to the priority queue accordingly by checking the distance from that Node to the other nodes and whether it was lesser than their already attributed distance. This improved the runtime of the algorithm because the queue was always small as possible. We also realized we should break the program once our destination node is explored, as otherwise we would be finding shortest paths to nodes we no longer need to.
We had trouble retracing the path once we had run the dijsktra algorithm. We tried retracing back from destination node in our queue till we found a neighbour of starting node. However we realized this just print all nodes visited by algorithm and is not what we need. We understood the need for an updater variable for each Node which will keep track of the latest Node that updates a Node. Later in lecture slides we saw this concept was given, but updater is called parent there. We then pushed and popped the parents from a stack to get the path in the right order.

-We also had trouble of how to allow priority queue to compare nodes. We thought about adding just the node distances. But we realized to add a CompareTo method in Node class which will compare the distance from source. We then added who nodes into the min heap.
We were having trouble figuring out how to use the longitudes and lattitudes. We used the code for the 'Harversine Formula' found at [https://github.com/jasonwinn/haversine/blob/master/Haversine.java] to calculate the weight of the edges based on their longitude and latitude. This was the only part of the pre-written code we used.

Extra Credit:
- We added Extra graphics to the map to make it much more informational. We added location pointers(map.png and map2.png) on the map of different colors at the starting and ending locations, and we also printed the distance in miles in the south panel. We also printed the starting and ending nodes in the south panel, along with an indication of what color pointer represents which node(yellow is starting node and purple is ending Node).

- We added the south panel which shows the starting and ending location, and it also has two input text boxes in which you could write new starting and ending locations and it will show the new path instantly on that same map. This features eliminates the need to rereun code in cmd for new nodes, as once code is run, new pair of nodes can be added in the text boxes of JFrame and Find button can be clicked to get results. 

-On the North panel we added a button for day and nightmode and pressing this button changes the background color and graph color making it seem like night and day mode.

- We have ensured that the map is always in the center by adding padding for a better user experience.

-We have improved upon the shortest algorithm and the description of how we did that is provided above.

-We have added an animation which shows a black line traversing the shortest path once it is drawn.
