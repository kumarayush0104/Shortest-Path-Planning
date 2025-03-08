# Modified Dijkstra Algorithm with Visiting Frequency
=====================================================

## Project Description

This project implements a modified version of Dijkstra's algorithm that incorporates visiting frequency into the pathfinding process. The algorithm is designed to find the shortest path between two nodes in a graph while considering the frequency of visits to each node.

## Motivation

The motivation behind this project is to create a more realistic pathfinding system that accounts for the impact of repeated visits on the cost of reaching a node. This can be particularly useful in scenarios where repeated visits to certain nodes incur additional costs or penalties.

## Method and Results

### Method

The modified Dijkstra's algorithm adjusts the cost of reaching a node based on its visiting frequency. The algorithm uses a priority queue to efficiently explore nodes with the lowest total cost, which includes both the edge weights and the penalty for visiting frequency.

### Results

The project provides an interactive interface where users can find paths between nodes and view the visiting frequency of nodes. The program saves visiting frequency data to a file for persistence across sessions.

## Features

- **Modified Dijkstra's Algorithm**: The algorithm adjusts the cost of reaching a node based on its visiting frequency.
- **Visiting Frequency Tracking**: The program tracks and updates the visiting frequency of each node.
- **Interactive Interface**: Users can interactively find paths between nodes and view the visiting frequency of nodes.
- **Data Persistence**: Visiting frequency data is saved to a file for persistence across sessions.

## Technologies Used

- **C++**: The project is implemented in C++ for efficiency and performance.
- **Standard Template Library (STL)**: Utilizes STL components like `vector`, `queue`, and `algorithm` for data structures and operations.

## Installation

To use this project, simply compile the C++ code using a compatible compiler (e.g., GCC) and run the executable.

## Usage

1. Compile the code using a C++ compiler.
2. Run the program.
3. Interact with the program by choosing options:
   - View visiting frequency.
   - Find a path between nodes.
   - Exit the program.

## Future Plans

### Short-Term Goals

1. **Optimization**: Improve the efficiency of the algorithm by exploring different data structures or optimization techniques.
2. **Visualization**: Integrate a visualization tool to display the graph and paths visually.
3. **Dynamic Graph Updates**: Allow users to dynamically add or remove nodes and edges from the graph.

### Long-Term Goals

1. **Integration with Real-World Data**: Use real-world data (e.g., traffic patterns) to simulate more realistic scenarios.
2. **Multi-Threaded Implementation**: Implement a multi-threaded version to handle large graphs more efficiently.
3. **Comparison with Other Algorithms**: Compare the performance of the modified Dijkstra's algorithm with other pathfinding algorithms.

## Contributing

Contributions are welcome! Please submit pull requests with clear descriptions of changes.

## License

None.

## Acknowledgements

We would like to express our sincere gratitude to all members of our project team for their tireless efforts and collaboration throughout this endeavor. Each member brought unique skills and perspectives that were instrumental in overcoming challenges and achieving our goals.

Special thanks to **Mithun Dutta**, **PQR**, and **ABC**, who contributed significantly to the development and implementation of this project. Their dedication and teamwork were invaluable.

We also appreciate the guidance and support from **Professor Abhik Mukherjee**, whose expertise and encouragement helped shape the direction and quality of our work.

## Credits

We used Dijkstra Algorithm, which helped us build our project.
