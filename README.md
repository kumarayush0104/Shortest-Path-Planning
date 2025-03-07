markdown
Copy
# Shortest Path Planning with Modified Dijkstra's Algorithm

## Description of the Algorithm and Code Functionality

This project implements a modified version of Dijkstra's algorithm to find the shortest path between two nodes in a graph. The modification includes a penalty based on the visiting frequency of nodes, which dynamically adjusts the path cost. The algorithm aims to balance the load across nodes by discouraging frequent visits to the same nodes.

The code also includes functionality to save and load the visiting frequency of nodes to/from a file (`visiting_frequency.txt`), allowing the program to maintain state across multiple executions.

## Code Structure Explanation

- **`saveVisitingFrequency`**: Saves the current visiting frequency of nodes to a file.
- **`loadVisitingFrequency`**: Loads the visiting frequency of nodes from a file, if it exists.
- **`modifiedDijkstra`**: Implements the modified Dijkstra's algorithm with a penalty based on visiting frequency.
- **`getPath`**: Retrieves the shortest path from the source to the destination and updates the visiting frequency of nodes along the path.
- **`main`**: The main function that initializes the graph, handles user input, and executes the algorithm.

## How to Use the Code

### Prerequisites
- A C++ compiler (e.g., g++).
- Basic understanding of graph theory and Dijkstra's algorithm.

### Compilation
To compile the code, use the following command:
```bash
g++ -o shortest_path_planning main.cpp
Execution
Run the compiled program:

bash
Copy
./shortest_path_planning
Input
The program will prompt you to enter a source and destination node.

You can also choose to view the current visiting frequency of nodes or exit the program.

Output
The program will output the shortest path from the source to the destination, including the path cost and the nodes visited.

It will also display the updated visiting frequency of nodes after each path calculation.

Example Graph Description
The graph used in this example has 7 nodes (0 to 6) with the following edges and weights:

0: (1, 2), (2, 4), (3, 5)
1: (0, 2), (2, 1), (4, 3)
2: (0, 4), (1, 1), (3, 2), (5, 6)
3: (0, 5), (2, 2), (4, 7), (6, 8)
4: (1, 3), (3, 7), (5, 4)
5: (2, 6), (4, 4), (6, 1)
6: (3, 8), (5, 1)

Description of visiting_frequency.txt File
The visiting_frequency.txt file stores the number of times each node has been visited. This file is updated every time the program exits, ensuring that the visiting frequency data is preserved across multiple runs of the program.

Customization and Improvement Suggestions
Graph Customization: Modify the adjacency list in the main function to represent a different graph.

Penalty Adjustment: Change the Penalty constant to adjust the impact of visiting frequency on path costs.

File Handling: Enhance the file handling to support multiple graphs or different file formats.

User Interface: Implement a more user-friendly interface, such as a graphical representation of the graph and paths.

Authors
This project is a group effort developed collaboratively. For more information, visit the GitHub repository.
