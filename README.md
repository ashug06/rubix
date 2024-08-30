# rubix




Rubik Cube (June 8th)

 https://youtu.be/cmeVjDpm2IE
 Rubik Cube - 2(June 15th)

https://youtu.be/PyzH7fokwsk



Terminology, Operations and Planar Representation

Terminology
Let’s start with some standard Rubik’s cube terminologies. These are common in the Rubik’s cube world and will come in handy throughout the project.

Cubie: One of the 26 mini-cubes that make up the whole cube. Each cubie can have either one, two, or three sides coloured.
Center Cubie: Cubies with only one side coloured and are present at the center of each side of the Rubik’s Cube. There are a total of 6 Center Cubbies. It is important to note that all center cubbies are statically positioned. No matter how you rotate/twist the Rubik’s Cube, the center cubbies will not change their positions relative to each other.
Edge Cubie: Cubbies which are coloured on two of their sides. There are a total of 12 edge cubbies. Eg: Red-Yellow Edge
Corner Cubie: Cubbies with three of their sides coloured. There are a total of 8 corner cubbies. Eg: White-Red-Blue Corner Cubie
Face: A side of a Rubik’s Cube made up of 9 cubies: 1 center, 4 edges, and 4 corners. There are six faces: front, back, left, right, up, and down.
Operations and Notation
After understanding all the terminologies, let’s get started with some standard operations and their notations that can be performed on a Rubik’s Cube.

To understand the operations, imagine holding a Rubik’s Cube in your hand (or actually holding one), with a White face facing you and a Red face facing up.

Since there are 6 sides/faces of a Rubik’s cube, you can perform 6 rotations by rotating any one of the 6 sides clockwise.



Now if you have correctly held the cube, we can label the faces as follows:

The face facing you would be Front (or F), in your case, it should be White.
The face facing up would be Up (or U), in your case, it should be Red.
The face facing down would be Down (or D), in your case, it could be Orange.
The face facing away from you, that is, the face opposite to the White face is Back (or B), in your case it could be Yellow.
The faces left and right to the White face are Left (or L) and Right (or R), in your case it could be Blue and Green respectively.
 
Now Look at the following Rotations



The above image shows twisting the Up (Red, in your case) side clockwise once.

 

We can rotate any of the faces clockwise once, thus, giving us 6 unique rotations. We denote these rotations by the first letter of the face, that is, F, U, L, D, R, B.

 

Notation	Meaning
F	Clockwise rotation of Front face
R	Clockwise rotation of Right face
U	Clockwise rotation of Up face
B	Clockwise rotation of Back face
L	Clockwise rotation of Left face
D	Clockwise rotation of Down face

 

Prime Rotations: We can rotate any of the 6 faces counter-clockwise once, thus, giving us 6 more rotations, denoted by the first letter of the Face and an apostrophe. These are F’, U’, L’, D’, R’, B’.
Double Rotation: Rotating a face clockwise (or anti-clockwise) will give another 6 rotations, denoted by a face letter followed by the number 2. These are F2, U2, L2, D2, R2, B2. 
Note that rotating the face clockwise twice and rotating the face anti-clockwise twice are the same thing. It'll result in the same type of face. So, without loss of generality, we're considering the double rotation operation as rotating the face twice clockwise.


 

This gives us a list of 18 possible moves we can make on a Rubik’s Cube:
 

F, F’, F2,

U, U’, U2,

L, L’, L2,

D, D’, D2,

R, R’, R2,

B, B’, B2


 

For trying out the simulation of rotations, you can go to:

https://ruwix.com/the-rubiks-cube/notation/advanced/

 

Planar Representation of a Rubik’s Cube
It’s difficult to visualize a 3D object (like a Rubik’s Cube) on a 2D surface like a monitor screen or paper. Therefore, we try to represent the Rubik’s Cube in a planar form as follows:



If you keep the Rubik’s Cube with White facing up and Red face facing you and then try to imagine as if the Rubik’s Cube is unfolding itself, an image similar to the above will be formed.

 

Look at the following example.


 




 

This planar representation is particularly helpful when we will try to print the Rubik’s Cube in our programs.




#Representing a Generic Cube in Code

Representation
Rubik’s cube is a real-world object. The first part of our project would be to try to take this real-world Rubik's cube and model it in some form that our computer can understand. This model should include everything necessary to define the unique state of a Rubik’s Cube. Also, it should support different operations like rotations (F, U2, B’, etc), so that we can write programs to solve them. Theoretically, we can model it in any form but we would ideally want to model it in a way that is fast to do operations/rotations upon.

Generic Cube
Going further, we are going to discuss various ways to model a Rubik’s Cube. But all of those implementations are going to have some common features. They all are going to support some common operations. So, instead of keeping all of these implementations completely independent, we can create a layout/blueprint for them which will state all things that the Model should implement. If you know about Object-Oriented Programming, you would recognize creating layouts/blueprints is a common theme. In this case, we would like to create abstract classes and pure virtual functions representing the Generic Cube.


 

If you want to read more about abstract classes and pure virtual functions, you can read it from here: 

https://www.learncpp.com/cpp-tutorial/pure-virtual-functions-abstract-base-classes-and-interface-classes/

 

If you are not familiar with Object-Oriented Programming in C++, you can spend some time learning the basics from 

https://www.learncpp.com/ (Chapter 12, 13, 16, 17, and 18).


 

We are going to create an abstract class of Rubik’s Cube, which would have certain common operations as virtual functions. We would take this Base Class and create Derived Classes for each representation. That way we can ensure a uniform structure to all our representations. 

Before going further try to list down things that you think would be common in each implementation.

Task 1: Generic Rubik’s Cube:
Write an abstract class of a Generic Rubik’s Cube that has the following operations as virtual functions:

All the 18 different rotations of the cube: F, Fprime, F2, U, Uprime, etc.
Print function: A function that takes the Rubik’s Cube and prints it in the Planar Representation Format.
Random Shuffle: A function that returns a randomly shuffled Rubik’s Cube which is solvable.
isSolved(): a boolean function that tells whether the current configuration of the Rubik’s Cube is solved or not.

 

Some Key Concepts
 

Not all permutations are solvable

It is important to realize that taking 9 * 6 = 54 colors and randomly assigning them to some cube side will not create a solvable Rubik’s Cube. For eg: an Edge Cubie with both sides as Red, or a Corner Cubie with sides white-yellow-red. We can never solve such a Rubik’s Cube configuration. It turns out we can only reach one-twelfth of the total possible permutations from a solved Rubik’s Cube (https://qr.ae/pGztcM for more info).

Therefore, in the Random Shuffle function, it is important to generate a Rubik’s Cube that is solvable. For this we would use the pre-existing operations that are implemented, that is, F, Fprime, etc. We would take a solved Rubik’s Cube and take a random operation out of the 18 possible total operations and apply it to Rubik’s Cube and repeat this process some number of times. This way we will ensure that the configuration that we created is solvable by legal moves.


 

Breaking the print function into two parts

Another key idea is about the print function. Instead of leaving the entire print functionality completely to the Derived classes, we can implement a generic print function in the abstract class itself. We can use a helper function ‘getColor’, which given a face, a row number, and a column number, would return the color of that face. And we can make this helper function virtual and leave its implementation to the Derived Classes. This would significantly reduce our efforts in writing the print functionality for each representation.


 

Reference Link for Task 1: 
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube.h
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube.cpp


https://youtu.be/apA2sK3c06k  Introductory Video and Task 1

Initial Setup And Version Control

 https://youtu.be/0w_n88BuEPk





 3D Array Representation

3D Array Representation
One of the most basic representations can be simply storing the colors of a face in a 3-dimensional array of size 6 x 3 x 3, which would look something like cube[SIDE][ROW][COL].

 

cube[ i ][ j ][ k ] → color of the ith side, jth row and kth col.
 

We can index the faces any way we'd like but we need to keep them uniform throughout the code. 

One way to index them is 


Up → 0 (White)

Left → 1 (Green)

Front → 2 (Red)

Right → 3 (Blue)

Back → 4 (Orange)

Down → 5 (Yellow)

 

Task 2: 3D Array Representation 
Write an implementation of 3D Array Representation of a Rubik’s Cube as described above. Derive this class from the Generic Rubik’s Cube class that we created in Task 1. Implement the necessary operations (all the virtual functions in the Generic Cube).

 

Reference Link for Task 2: 
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube3dArray.cpp

1D Array Representation

1D Array Representation
Another way to represent the Rubik’s Cube would be a single array of 54 characters. Each position holds the color of the particular cubie’s side. Since there are 6 sides and each side has 9 stickers/colors, the size of the array is going to be 6 * 9 = 54.
 

cube[ i ] → color of the i-th cubie side, when indexed sequentially
 

The reason for doing this is, generally speaking, 1D arrays are easier to store and operations on them are slightly faster.
 

You can index the faces, rows, and columns any way you like. But an intuitive way would be to do it the same way done above in 3D array representation. Faces would be indexed like: {Up, Left, Front, Right, Back, Down}. Rows and Columns would be indexed for each face from top to bottom and left to right.

 

Task 3: 1D Representation
Write an implementation of 1D Array Representation of Rubik’s Cube as described above. Derive this class from the Generic Rubik’s Cube class that we created in Task 1. Implement all the necessary operations (all the virtual functions).

 

 

Reference Link for Task 3:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube1dArray.cpp





 Bitboard Representation

Bitboard Representation (6 64-bit Integers)
After the array representations of Rubik’s Cube, let’s come to something more faster and compact, that is, bits. Let’s see how we can use bits to represent the Rubik’s Cube.

There are 6 unique colors in a Rubik’s Cube. For every color, let’s try to represent it in an 8-bit format. Out of the 8-bits, only one bit would be set (1), and its position would define the color. For example, we encode the colors as follows: 

 

Color	8-bit Format
White 	00000001
Green 	00000010
Red 	00000100
Blue 	00001000
Orange 	00010000
Yellow 	00100000
 

White has its 0th-bit set. Green has its 1st-bit set. And so on. The last two bits would always be 0 because there are only 6 colors.

Note that we are keeping the order of the colors and faces uniform in all the representations. This makes it simple to implement and remember things. 

 

The order we use is

Color	White	Green	Red	Blue	Orange	Yellow
Face	Up	Left	Front	Right	Back	Down
 

We are done with representing a color. Let’s try to represent a face. 

 

A face has 9 colors/stickers. Since the center stickers are always stationary, we only need to store 8 out of the 9 stickers. We can use the 8-bit format for each sticker.

8 (stickers) * 8 (8-bit color) = 64 bits. 

 

Therefore, each face can be represented using a 64-bit integer.

The first 8 bits of the integer would represent the 0th index sticker. The next 8 bits would represent the 1st index sticker. And so on.

 

We index the stickers in a face in a clockwise rotational fashion, like below:

0    1    2

7    _    3

6    5    4

 

So finally an example face would look something like this: 

64-bit format: 

Color	G	W	Y	O	B	R	G	W
Bits	00000010 	00000001 	00100000 	00010000 	00001000 	00000100 	00000010	00000001 
Index	7	6	5	4	3	2	1	0
 

The 64-bit integer would be:

00000010 00000001 00100000 00010000 00001000 00000100 00000010 00000001

In the Decimal, the above representation is equivalent to the number 144431916278612481.

 

This face would look something like this:

W    G    R

G     _     B

W    Y    O


 

We can create an array of 6 64-bit integers, bitboard[6],  to represent the whole cube.


bitboard[ i ] → the 64-bit integer representing the ith face.


Task 4: Bitboard Representation
Write an implementation of the bitboard representation of the Rubik’s Cube as described above. Derive this class from the generic Rubik’s Cube we designed in Task 1. Implement all the necessary functions (all the virtual functions).


Some Key Concepts
Keeping indices of the cube in a clockwise rotational fashion

This idea helps us greatly in rotating a particular face. While doing any operation this idea makes it very easy to do a face rotation. We just need to rotate the 64-bit integer by 16 bits and the face would be rotated. Next, we can adjust the adjacent sides of the face manually.


For example if want to rotate the front face and it looks something like this:

W    G    R

G     _     B

W    Y    O


Which sequentially translates to : 

Color:    W     G     R     B     O     Y     W     G

Index:    0      1      2     3     4      5      6      7


After rotation the face would look something like:

W     G     W

Y      _      G

O      B     R


Which sequentially translates to:


Color: W G W G R B O Y

Index: 0 1 2 3 4 5 6 7


If you look carefully, we have just shifted the number by two indices (8 bits * 2 = 16 bits), and put the last two indices in the first.


Caution: Don’t get confused by seeing indices written here in increasing order from left-to-right. In actual, bit form they will be opposite, as the 0th index would occupy bits from 0 to 7, 1st index from 8 to 15, and so on.


This makes it very easy to rotate the face. But we still need to adjust the rest of the faces that got affected due to rotation. 

In case of a F move, some of the top cubbies will come to right, some right cubbies to down, down to left, and some left cubbies to top. We need to adjust those manually in code.

 

 
Reference Link for Task 4: 
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCubeBitboard.cpp



 Representing the Rubik's Cube in different ways

https://youtu.be/IuzjBGFOZjM
Basic Class Structure and Output Expectations

https://youtu.be/DqO2uHpgtUs
Introduction and some preparatory work

Solving using Algorithms
We are done with representing the Rubik’s Cube in different ways. Let’s start with trying to solve the Rubik’s Cube. But before that, you should know some things about the Rubik’s Cube. There are 43,252,003,274,489,856,000 possible states of Rubik’s Cube. Despite that, in 2010 it was shown that any Rubik’s Cube configuration can be solved in 20 moves or fewer. This is an important fact that will come in handy later. Now let’s start with the solving part.

We can use our Human algorithm (the way humans solve the cube) and program it. Our program will solve it within milliseconds. But it will probably do 100s of moves to solve the cube. What we are interested in is to solve the cube in a very small number of moves. And we want the program to output those moves/operations done to solve the cube. 


 

Therefore, what we can do is we can define one particular configuration of Rubik’s Cube as a state and we can transition to other states by doing some operations. This structure is very similar to a Graph. In fact, many similar problems (like problems in AI) can be solved using graphs. We can start with our initial Jumbled Cube as our starting state and try to reach the Final Solved state (the Goal state). We can use Graph Algorithms to traverse this graph.

A set of graph algorithms that we can use are:

Depth-First Search (DFS)
Breadth-First Search (BFS)
Iterative-Deepening Depth-First Search (IDDFS)
 
All these algorithms are very similar. All of them: visit a node, mark the node visited, and then proceed to visit its neighbours in some order.

But there is a problem here. While solving conventional problems, where the nodes of a graph were integers, we were able to keep the track of visited nodes using an array or a map. How are we supposed to keep track of visited states for an entire Rubik’s Cube?

 

We can use unordered_map<RubiksCubeClass, bool>
 

This unordered_map will map the entire Rubik’s Cube states to a boolean value. To be able to use unordered_map with a custom user-defined class, we need to define the following two things:

A hash function: this must be a class that overrides operator() and calculates the hash value given an object of the key-type.
A comparison function for equality: this is required because the hash cannot rely on the fact that the hash function will always provide a unique hash value for every distinct key (i.e., it needs to be able to deal with collisions), so it needs a way to compare two given keys for an exact match. This can be done by overloading the operator==() for our custom classes.
 
Along with this, we would also want to implement the operator=(), assignment operator for our classes. This is because we would be needing to create copies of the Rubik’s Cube and we don’t want to create Shallow copies.

 

You can read more about :

Overloading operator==() : https://www.learncpp.com/cpp-tutorial/overloading-the-comparison-operators/

Overloading operator=(): https://www.learncpp.com/cpp-tutorial/overloading-the-assignment-operator/

Hash Functions and Using custom classes with unordered_map: https://www.geeksforgeeks.org/how-to-create-an-unordered_map-of-user-defined-class-in-cpp/


 

Task 5: Hash Functions and overloading operator==() and operator=() 
Implement the following for all three representations of Rubik’s Cube (3dArray, 1dArray and Bitboard)

Custom Hash Function
Overload Comparison operator ( operator==() )
Overload Assignment operator ( operator=() )
Check the above by making an unordered_map of all three representations.


 

Reference Link for Task 5:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube3dArray.cpp

https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube1dArray.cpp

https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCubeBitboard.cpp



DFS Solver

Making the Solvers:
After implementing the above 3 things, we are all set to build our first solver. We would like to create a class of a solver that would take in the Rubik’s Cube. We should then be able to call the solve() method of that class, which would return us the moves/operations needed to solve the Rubik’s Cube. But there is an issue. We want that solver to be able to take the Rubik’s Cube in any representation. We don’t want to write 3 different solvers for the 3 representations. We want the generic solver to take in the Rubik’s Cube in any representation along with it’s Hash function, and solve the Rubik’s Cube. This is where the concept of Templates comes into the picture.

 

Templates are a way of making your classes more abstract by letting you define the behavior of the class without actually knowing what datatype will be handled by the operations of the class. Thus, we can define the solvers without actually specifying the datatype (Rubik’s cube representation in our case).

To read more about templates and it’s syntax : https://www.learncpp.com/cpp-tutorial/template-classes/


 

Depth-First Search Solver:
We will start with the easiest one, a DFS solver. This solver will take the initial Rubik’s cube and do a DFS until it finds the solver state of the cube. But with DFS what can happen is, it can keep going into depths of the graph and actually never find a solution (or find a very long solution, thousands of moves, in a practically infinite amount of time). Here, we can use the fact that all Rubik’s Cube are solvable in 20 moves or fewer. Therefore, we can restrict our DFS to a max depth of 20.  We can also keep this max depth as a Hyper-parameter for testing purposes.


 

Task 6: DFS Solver
Implement a DFS solver which takes a Rubik’s cube along with the max search depth (hyper-parameter). And upon calling the solve() function, it solves the Rubik’s cube and returns the steps done to solve the cube. Make this solver generic (compatible with all 3 representations) by making the use of template classes.

Try and experiment with this solver by doing a random shuffle of 5 or 6 and setting the max depth of the solver upto 7 or 8.


 

Caveat: 
If you have implemented the solver in a normal DFS way, and you try and experiment with different amounts of random shuffles and search depths, you will find that sometimes the DFS solver is not returning an answer even if the search depth > random shuffle.

For eg: If you try to set the random shuffle to 6 and keep the max search depth of the solver as 7 or 8, it might happen the solver is not finding a solution at all. Which should not happen because our solution should exist at depths <= 6 only. Then why is this happening? Try to think what could be the reason behind it.


 

It turns out we are using two types of restrictions that are causing this problem. We are trying to limit the amount of exploration by not visiting the already visited nodes. Also, we are restricting the solver to not go beyond the depths of 20. These two are not a problem individually but are causing a problem when used together. What is happening is:

The solver goes to some nodes/states through a long path.
It then marks these nodes visited.
It continues to go deep and reaches the maximum depth.
It returns without finding a solution
Now it tries to come to the same nodes with a shorter path, but these nodes are already visited. Thus, it doesn’t explore them any more.
But if the solver would have explored these nodes with a shorter path, it would find the solution at a depth <= max depth.
This phenomenon occurs often enough that you will see this happen in your experiments with the solver.
 

To deal with this problem we can remove the visited map. We would allow our solver to revisit nodes. This will increase the complexity of our solver, but it will then at least be able to solve the Rubik’s Cube. 


 

Reference Link for Task 6:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Solver/DFSSolver.h




 BFS Solver

Breadth-First Search Solver:
Next comes the BFS Solver. A BFS Solver will work very similarly to a DFS Solver, just using the BFS strategy to search the solution space. Since, BFS is an optimal solver, that is it is going to find the minimum number of moves needed to reach the Goal state, we don’t need to explicitly specify the max search depth. It will automatically solve the Rubik’s Cube in <= 20 moves.


 

Task 7: BFS Solver
Implement the BFS Solver, which takes in a jumbled Rubik’s Cube. And upon calling the solve() member function, it returns the steps (minimum) needed to solve the cube. Make this solver generic (compatible with all 3 representations) by making the use of template classes.

Try and experiment with different Random Shuffles, upto 6 or 7.


 

Reference Link for Task 7: 
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Solver/BFSSolver.h



 IDDFS Solver

Iterative Deepening Depth-First Search (IDDFS) Solver:
We created two solvers till now, namely, BFS and DFS solvers. But these two are not very efficient when it comes to traversing very large and very deep graphs (like Rubik’s Cube state space). This is because of the following:

DFS: DFS first traverses nodes going through adjacent to root, then next adjacent. The problem with this approach is, if there is a node close to root, but not in the first few subtrees explored by DFS, then DFS reaches that node very late. Also, DFS may not find the shortest path to a node (in terms of number of edges).
BFS: BFS goes level by level, but requires more space. The space required by DFS is O(d) where d is the depth of the tree, but space required by BFS is O(n) where n is the number of nodes in the tree (Why? Note that the last level of the tree can have around n/2 nodes and second last level n/4 nodes and in BFS we need to have every level one by one in queue).

 

IDDFS combines depth-first search’s space-efficiency and breadth-first search’s fast search (for nodes closer to root).

 

How does IDDFS work?
IDDFS calls DFS for different depths starting from an initial value. In every call, DFS is restricted from going beyond given depth. So basically we do DFS in a BFS fashion.

An important thing to note is, we visit top level nodes multiple times. The last (or max depth) level is visited once, second last level is visited twice, and so on. It may seem expensive, but it turns out to be not so costly, since in a tree most of the nodes are in the bottom level. So it does not matter much if the upper levels are visited multiple times.

You can read more about IDDFS from here: https://en.wikipedia.org/wiki/Iterative_deepening_depth-first_search


 

Task 8: IDDFS Solver
Implement the IDDFS Solver, which takes in a jumbled Rubik’s Cube. And upon calling the solve() member function, it returns the steps/moves needed to solve the cube. Make this solver generic (compatible with all 3 representations) by making the use of template classes.

Try and experiment with different Random Shuffles, upto 6 or 7.


 

Reference Link for Task 8:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Solver/IDDFSSolver.h


IDDFS Solver

Iterative Deepening Depth-First Search (IDDFS) Solver:
We created two solvers till now, namely, BFS and DFS solvers. But these two are not very efficient when it comes to traversing very large and very deep graphs (like Rubik’s Cube state space). This is because of the following:

DFS: DFS first traverses nodes going through adjacent to root, then next adjacent. The problem with this approach is, if there is a node close to root, but not in the first few subtrees explored by DFS, then DFS reaches that node very late. Also, DFS may not find the shortest path to a node (in terms of number of edges).
BFS: BFS goes level by level, but requires more space. The space required by DFS is O(d) where d is the depth of the tree, but space required by BFS is O(n) where n is the number of nodes in the tree (Why? Note that the last level of the tree can have around n/2 nodes and second last level n/4 nodes and in BFS we need to have every level one by one in queue).

 

IDDFS combines depth-first search’s space-efficiency and breadth-first search’s fast search (for nodes closer to root).

 

How does IDDFS work?
IDDFS calls DFS for different depths starting from an initial value. In every call, DFS is restricted from going beyond given depth. So basically we do DFS in a BFS fashion.

An important thing to note is, we visit top level nodes multiple times. The last (or max depth) level is visited once, second last level is visited twice, and so on. It may seem expensive, but it turns out to be not so costly, since in a tree most of the nodes are in the bottom level. So it does not matter much if the upper levels are visited multiple times.

You can read more about IDDFS from here: https://en.wikipedia.org/wiki/Iterative_deepening_depth-first_search


 

Task 8: IDDFS Solver
Implement the IDDFS Solver, which takes in a jumbled Rubik’s Cube. And upon calling the solve() member function, it returns the steps/moves needed to solve the cube. Make this solver generic (compatible with all 3 representations) by making the use of template classes.

Try and experiment with different Random Shuffles, upto 6 or 7.


 

Reference Link for Task 8:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Solver/IDDFSSolver.h


Discussing Different Solvers


https://youtu.be/qt-X85T3z0k
Discussing DFS Solver code and Testing
https://youtu.be/e5zhhBCGGm4




















Understanding the IDAstar Algorithm

IDA* Solver - Korf’s Algorithm:
Now comes the centerpiece of this project, the IDA* solver using Korf’s Algorithm. Korf, in his research paper, introduces an Algorithm to solve the Rubik’s Cube in optimal number of moves using the IDA* Algorithm which combines the A* algorithm with IDDFS and uses pattern databases as a heuristic. Wow, that was a handful of things. Let’s look at each one of them one by one.


 

A* Algorithm:
A* algorithm is graph traversal algorithm, similar to Dijkstra’s algorithm, the only difference being that it uses guided search. In Dijkstra’s, we used to explore the nodes which were closest (minimum weight) to the source but we didn’t have any idea if we were going in the right direction or not. We didn’t have any estimate as to how far the goal state is from a particular node. 

This is where A* differs. It uses a metric (called heuristic) to get an estimate of how far the current node is from the goal state. This heuristic need not be exact but can be an underestimate of the actual distance to the goal state. It combines this heuristic with the distance travelled from the source to the current node, and prioritises nodes which have the sum of heuristic + distance travelled as minimum. Formally,

 

g(n) → Distance from source node to current node

h(n) → Estimate of distance from current node to goal node
 

Then,

f(n) = g(n) + h(n)


 

A* prioritizes the nodes which have minimum f(n), thus, exploring them first.

 

For more info:

https://en.wikipedia.org/wiki/A*_search_algorithm

https://www.simplilearn.com/tutorials/artificial-intelligence-tutorial/a-star-algorithm


 

Heuristic:
You might have many questions after reading the previous paragraph. Mostly, about the heuristic. What is this heuristic? If we already have the distance of all the nodes to the goal node, in the form of heuristic, then what is the point of the graph traversal? How did we obtain the heuristic in the first place?

Let us answer these questions one by one.

Heuristic is nothing but an estimate (or a guess) of how far a particular node is from the goal node. This can be the exact distance or an underestimate (you should not overestimate). A* uses this estimate/guess to find the optimal path from the source node to the goal node. Now, this heuristic can be pre-computed. The way we get this heuristic can be different for different problems. In our case, we create pattern databases to use as a heuristic.


 

Pattern Databases:
Pattern Database is probably the most important part of this algorithm. A Pattern Database will store the number of moves it will take to reach the solved/goal state of the Rubik’s cube. Of course we cannot create the pattern database for all possible states of the Rubik’s cube (43 quintillion configurations). This is where we can create Corner Pattern Database and Edge Pattern Database, as suggested by Korf in his research paper.

 

Corner Pattern Database: This database will contain the number of moves required to solve the corners of the Rubik’s Cube, that is, assume that beside the 8 corners, all other cubbies are blank (or solved) at all times, and then solve the Rubik’s cube.
Edge Pattern Database: This database will contain the number of moves required to solve the edges of the Rubik’s Cube, that is, assume beside the 12 edge cubbies, all other cubbies are solved (or blank) at all times, and then solve the Rubik’s cube. To reduce the number of permutations Korf suggests using an Edge database considering 6 edges and another database considering the other 6 edges.
 
For simplicity's sake (also considering our system requirements), we will only build Corner Pattern Database. You can, however, create an edge corner database too, if you want to. More details about the Pattern Database are discussed in future.


 

IDA* Algorithm:
IDA* is the actual algorithm that we use to create the solver, as suggested by Korf. This algorithm is just a combination of A* algorithm and IDDFS algorithm. 

We start by running the A* algorithm with a certain bound, that is, the f(n) value for a particular node should not exceed that max bound. If it exceeds, we simply prune the branch. 
Along with that, we keep a track of the nearest (minimum) f(n) that we encountered that exceeded our current maximum bound. It would simply be the minimum of all the f(n) of nodes that were pruned. Let us call this the next_bound.
If we find the goal state then we stop the algorithm. Otherwise, we re-run the A* algorithm with the max bound set to next_bound that we calculated.

 

This small addition to our A* algorithm will make it a much faster IDA* algorithm.

You can read more about all this in Korf’s original research paper:

https://www.cs.princeton.edu/courses/archive/fall06/cos402/papers/korfrubik.pdf


 

Implementing the IDA* Solver
It’s finally time to implement the IDA* solver. Let’s start by implementing a basic solver without a heuristic so that we have some code in my place and can check our core algorithm without worrying about the pattern databases. For now, we can keep the heuristic for every rubik’s cube configuration as 0. Even using 0 as a heuristic, the algorithm should still work (just not as efficiently) because we are allowed to underestimate the heuristic.


 

Task 9: IDA* Solver
Implement the IDA* Solver, which takes in a jumbled Rubik’s Cube. And upon calling the solve() member function, it returns the steps/moves needed to solve the cube. Make this solver generic (compatible with all 3 representations) by making the use of template classes. To get the estimate / heuristic, implement a dummy class, in which upon passing a Rubik’s Cube, it returns the estimated distance to solved / goal state. For now, set the distance returned from that dummy class to be zero. Try and experiment with solver, by trying to solve a Rubik's Cube that is jumbled 5-6 times.


 

Reference Link for Task 9:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Solver/IDAstarSolver.h

Workflow of IDAstar Solver

https://youtu.be/2Zcr9rJlsp0
Getting started with Pattern Database

Creating the Corner Pattern Database:
Let’s take a look at the Corner Pattern Database now. This database will store the number of moves it will take to solve the corners of a jumbled Rubik’s Cube. There are 8 corner cubbies, and each cubie can acquire any of the 8 positions, giving us 8! different possible permutations. Each of the corner cubie can be oriented in 3 different directions - any of three stickers facing up. But the orientation of the 7 cubies dictate the orientation of the 8th cubie. This is part of the laws of the cube (https://www.ryanheise.com/cube/cube_laws.html).


This gives us a total of 8! * 3^7 possible ways to jumble the corners of Rubik’s cube. These 88,179,840 states can be then iterated upon (do a BFS). Another fact that we can use here is that all these states are solvable in 11 moves or fewer. Thus, the answer of these states can be stored in a nibble (4 bits). This gives a total size of 88 million * 4/8 = 42 MB of data. This gives us a neat way to store the answers (heuristic values) for different cube configurations but how will we search through this? How would we know which value belongs to which configuration?

 

This is where the concept of Sequentially Indexing Permutations comes into play. This is going to get a little mathematical but don’t worry, we’ll use this concept as a black box. It turns out, we can sequentially index permutations, meaning we can convert a permutation to a number, like a hash. Not only that they will be sequential in nature and not random large numbers. That means that we can store the answers in an array, where the index denotes the sequential index of the Rubik’s cube (permutation).
 

Let “idx” be the sequential index of the permutation of a Rubik’s cube, then

Arr[ idx ] → Number of moves it takes to solve the corners of the Rubik’s Cube 


 

Before we talk more about this, let’s first try to implement what we already know.

Nibble Array:
A nibble is basically half a byte, or 4 bits. Our answers can be stored in 4 bits. But C++ does not have a 4-bit data type. It however has a data type for 8-bits, “uint_8”. We can use this data type to create our own custom nibble array, which would support all the operations we would need to store and use the 4-bit values. The first 4 bits of the 8 bits would hold the first value, while the last 4 bits would hold another value. This can be easily implemented using bit manipulation. Therefore,
 

Arr[ idx ] → would hold two values, one of position “2*idx” (in its first 4 bits) and one of “2*idx + 1” (in its last 4 bits).
 

This nibble array is actually optional because you can store answers in 8-bit integers by just ignoring the last 4 bits. But using Nibble array significantly improves our memory requirements by a factor of 2. From 84 MB → 42 MB. We care about this memory because we need to load this entire data into memory (RAM) to get the ability to Random Access the elements.

Task 10: Nibble Array
Implement a data structure in the form of a class, which can store 4-bit values using 8-bit integers (uint_8). List down the operations we would require to do on this array and implement them using bit manipulation. Some of the methods can be:

Initialize the array of a particular size with a particular value
Get the value at a particular position
Set the given value at a particular position
 
Reference Link of Task 10:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/NibbleArray.h
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/NibbleArray.cpp

 

Pattern Database: Base Class
You can try to implement multiple different databases (like corner, 6-edge, 7-edge). All of these will have some common functionalities. Therefore, we will create a base-class of Pattern Database that would use the Nibble Array that we created in previous step to store the data and do the following operations:

Initialize the database (internal array) with a given value
Write the current array to a file
Read the values of the array from a file and store them
Given a cube, get its Database Index (the index at which its answer would be stored). This function / method would be different for different databases. Thus, this would be a pure virtual function.
Given a cube and a heuristic value, set its heuristic value in the array.
Given a cube, return its heuristic value stored in the array.
You can implement any other functions / methods that you require.

Task 11: Pattern Database Base Class
Implement the Pattern Database class that will act as a base class as discussed above. Also, implement all the necessary functionalities needed. Use the Nibble Array and any other member variables to store the information about the database.
 

Reference Link for Task 11:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/PatternDatabase.h
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/PatternDatabase.cpp

Starting with Pattern Databases


https://youtu.be/NgaVQ8EPjlk
Corner Pattern Database using Permutation Indexer

Corner Pattern Database using Permutation Indexer:
Now let’s implement the Corner Pattern Database. We will inherit the PatternDatabase class to implement this class. The only thing now left to implement is the getDatabaseIndex() method. This method should return the calculated index of a given Rubik’s Cube. To calculate this index we will use the Permutation Indexer as a black box. Permutation Indexer takes in an array of numbers (permutation) and returns it’s corresponding index. In our case, we first need to get the rank/index of the corner permutations then combine it with corner orientations to get the actual rank/index.

 

Index = (index_of_permutations * (3^7)) + index_of_orientations
 

We’ll discuss how to get this rank/index but first we need to get the index and orientation of corners of a Rubik’s cube. We can implement these functions in base class so that it works with every representation of Rubik’s Cube. Index and orientation of a corner are nothing but a number from 0→7 and 0→2 respectively. For indices, assume the corners of a Rubik’s cube to be numbered from 0→7. Now for a jumbled Rubik’s cube we just need to find the index of the corner kept at that corner. Similar is for orientation, we just need to get which orientation that corner is in.

Task 12: Index Permutation and Orientation of Corners
Implement the member functions in the base class of Rubik’s Cube that would give the index and orientation of the corner:

getCornerIndex(): Given a Rubik’s cube and a corner, find which corner is placed there (0, 1, 2, 3, 4, 5, 6, 7).
getCornerOrientation(): Given a Rubik’s cube and a corner, find the orientation of that corner (0, 1, 2)
Reference Link for Task 12:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube.h
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Model/RubiksCube.cpp

 

Using the Permutation Indexer:
Now to use the permutation indexer you need to add the following files to your code:

https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/math.h
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/math.cpp
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/PermutationIndexer.h

 

Files math.h and math.cpp include the utility functions to perform some mathematical operations. PermutationIndexer.h holds the class which can give us the index for a particular permutation.

You can refer to the following files to see how to use the permutation indexer and combine the ranks of corner index and corner orientation:

https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/CornerPatternDatabase.h
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/CornerPatternDatabase.cpp

 

Task 13: Getting Database Index
Implement the CornerPatternDatabase class and its getDatabaseIndex() method by combining the ranks of corner index permutation and corner orientation. Use the PermutationIndexer class as a black box.

Finalizing the IDAstar Solver

Creating the Corner Database Maker:
We are almost done. The only task now left is to actually do the BFS and store the values in a file. After the Database is created then we can make the changes in our original IDA* solver to give the real estimate instead of 0. To create this Database, we can create a DBMaker class or you can code it any way you want. Creating this database is a bit system dependent. You would need to experiment with the memory requirements and upto which depth would you be able to handle to compute states in the BFS. Start from a smaller number like 4-5 and try to create multiple databases with increasing depth. Suppose you set the max BFS depth to be 5, you can then set the rest of the indices to 6, because all other states would be at least 6 moves away and we are allowed to underestimate.
 

Task 14: Create the DBMaker
Implement the actual BFS code to calculate and store the heuristic values in a file. Use the CornerPatternDatabase class to set the values and write to a file. Also, pass the max depth as a parameter so that you can experiment with different databases.

Reference Link for Task 14:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/CornerDBMaker.h
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/PatternDatabases/CornerDBMaker.cpp

 

Task 15: Make the changes in IDA* solver
Finally, instead of a dummy value of 0, read the heuristic value using the CornerPatternDatabase from a file. After changing the estimated value, experiment with the solver to see if it is working properly.


 

Reference Link for Task 15:
https://github.com/shubhampatil11/rubiks-cube-solver/blob/main/Solver/IDAstarSolver.h

Completing the Corner Pattern Database and the Solver

https://youtu.be/28gLKvmZuVg

Key Learnings from this project

Key Learnings from the project:
We learned how to take a real world object, like a Rubik’s Cube, and model it into something that the computer can understand.
We learned how to take a larger problem, like the complete Rubik’s Cube solver, and break it down into smaller problems, using basic models and controllers, that is, Rubik’s cube representations and solvers.
We learned how to break down multiple representations into classes and create base classes that can be further extended. Namely, creating Rubik’s Cube base class and Pattern Database Base class.
We also learned many practical examples of Object-Oriented Programming in use, like the following:
Classes and Objects
Virtual Functions and Abstract Classes
Inheritance
Operator Overloading
We learned how path finding algorithms like BFS, DFS, IDDFS and IDA* can be used to solve real world problems related to AI. Many more problems in the field of AI can be solved using these algorithms.
We learned about the concept of Heuristic Search Algorithms like A* and IDA* and how Pattern Databases can be created to provide that heuristic.
Miscellaneous things we learned along the way:
How unordered_map<> works for custom objects
How to create custom hash functions
How bits can be used to store information
How to save and load files 
The basic idea of Black boxing, where we can give an input and expect a certain output from the Black Box (in our case, the Permutation Indexer)


How to add this project to Resume

How to add the project to resume:
We are done with the project. Now it’s time to add this project to our resumes and make them shine. We need to add it in such a way that the interviewer (or whoever sees your resume) notices it immediately and becomes genuinely interested in this project. As someone rightly said, in the context of resume building of course – “The saddest thing you can do for yourself is achieve many great things and not be able to present them properly”.
 

We can keep a few points in mind while adding the project to our resume

Give a nice and bold heading to the project that instantly convey what the project is about
Make sure to add links to the project code, and if the project is deployed somewhere make sure to add the link to that as well. Adding the link to source code and the deployed site gives the proof of work and the person reviewing can see for themselves what work you have done.
Sentence structuring: 
Use the structure : Action verb + Impact + How
For eg: Achieved 99.32% accuracy for classification of images of transient objects by randomised flipping, cropping and rotation
For action verbs, in our case, you can use : Implemented, achieved, modelled. You should avoid using : made, completed, worked on, etc.
Use numbers and metrics. Numbers create an impact and instantly shows what you have achieved. In our case, we can use multiple metrics, like the time taken by our program to solve the Rubik’s cube
Highlight the important keywords, like the Algorithms you have used, the numbers, metrics, figures, etc.

 

An example could look something like this:



Questions that can be asked in Interview

Questions that can be asked on the project:
You might be asked many questions on this project during your interview. They can range from purely technical to behavioural questions. Therefore, you should know all the ins and outs of the project. Following are some questions that were asked in real interviews. See if you can answer them.


 

Q1. As Rubik’s cube is a real world object, how did you model it into your code?


 

Q2. In the real world, we can rotate, flip and turn the Rubik’s cube in many different ways. How did you incorporate that into your program?


 

Q3. While creating the project, how did you know if the Rubik’s cube that was being formed was correct? Did you have to just imagine it by seeing numbers or did you use some way to visualise it?


 

Q4. Did you use some pre-existing library for representing the Rubik’s cube?


 

Q5. What are these solvers? What exactly do they do?


 

Q6. So you’re saying solvers use graphs? What does the nodes and edges of this graph mean?


 

Q7. If you are essentially creating a graph, is there a limit to the structure of this graph?


 

Q8. While making this project, did you take any risk that failed in the end? 


 

Q9. Which part of the project did you find the most challenging? How did you tackle it?


 

Q10. Do you have plans to extend this project? If yes, what exactly are you planning?

