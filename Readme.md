# Campus Maintenance Scheduler

## Project Overview

This project is a comprehensive C++ application that implements an intelligent campus maintenance scheduling system using a modified Dijkstra's algorithm. The system dynamically calculates cleaning priorities and generates optimal maintenance routes based on various factors including location importance, cleanliness status, and visiting frequency.

## Features

### Core Functionality
- **Intelligent Pathfinding**: Modified Dijkstra's algorithm that considers multiple factors for optimal route planning
- **Dynamic Priority Calculation**: Real-time calculation of cleaning priorities based on:
  - Location importance (1-10 scale)
  - Cleanliness status (0-100%)
  - Time since last cleaning
  - Visit frequency
  - Road difficulty factors

### Data Management
- **File I/O Operations**: Save and load campus data from text files
- **Admin Authentication**: Password-protected configuration reset
- **Data Persistence**: Automatic backup of campus state

### User Interface
- **Interactive Menu System**: Easy-to-use command-line interface
- **Real-time Status Display**: Comprehensive campus status reporting
- **Simulation Capabilities**: Multi-day maintenance simulations

## Project Structure

### Main Components
- **`Improved.cpp`**: Primary application with complete campus maintenance system
- **`main.cpp`**: Modified Dijkstra algorithm implementation (standalone version)
- **Data Files**:
  - `campus_data.txt`: Default campus configuration
  - `campus_backup.txt`: Persistent data storage
  - `admin.txt`: Admin credentials (password: kumarayush0104)
  - `visiting_frequency.txt`: Node visit tracking data

### Key Classes
1. **`Location`**: Represents campus locations with attributes like importance, cleaning frequency, and cleanliness status
2. **`Path`**: Defines connections between locations with distance, travel time, and difficulty factors
3. **`CampusMap`**: Manages locations, paths, and provides utility functions
4. **`ModifiedDijkstra`**: Enhanced pathfinding algorithm with priority-based weighting
5. **`MaintenanceScheduler`**: Generates daily maintenance routes and manages simulations

## Algorithm Implementation

### Modified Dijkstra's Algorithm
The algorithm incorporates multiple weighting factors:

```cpp
double weight = (alpha * edge.distance) + 
               (beta * edge.difficulty) + 
               (gamma * visitFactor);
weight *= (2.0 - priorityFactor);
```

Where:
- `alpha`: Distance weight (default: 0.6)
- `beta`: Difficulty weight (default: 0.3)  
- `gamma`: Visit frequency weight (default: 0.1)
- `priorityFactor`: Location priority consideration
- `visitFactor`: Penalty for frequently visited nodes

### Dynamic Priority Calculation
```cpp
double priority = (importance * 0.3) + 
                 ((100 - cleanliness) * 0.4) + 
                 (visitPriority * 0.1) + 
                 (timeFactor * 0.2);
```

## Installation & Setup

### Prerequisites
- **Windows OS** (primary development environment)
- **C++ Compiler**: g++ from MinGW (C++11 or later)
- **Command Line Proficiency**: Basic terminal navigation skills

### Compilation Instructions

1. **Install MinGW**:
   ```bash
   # Download from http://www.mingw.org/
   # Add MinGW bin directory to system PATH
   # Verify installation: g++ --version
   ```

2. **Compile the Application**:
   ```bash
   # For the main campus maintenance system:
   g++ Improved.cpp -o campus_maintenance.exe
   
   # For the standalone Dijkstra implementation:
   g++ main.cpp -o dijkstra_demo.exe
   ```

### Required Data Files
Ensure these files are present in the executable directory:
- `campus_data.txt` - Default campus configuration
- `admin.txt` - Admin credentials file
- `campus_backup.txt` - Will be created automatically

## Usage

### Running the Application
```bash
# Run the campus maintenance system
campus_maintenance.exe

# Run the Dijkstra demonstration
dijkstra_demo.exe
```

### Main Menu Options
1. **Find Optimal Path**: Calculate best route between two locations
2. **View Campus Status**: Display current cleanliness and priority status
3. **Run Simulation**: Execute multi-day maintenance simulation (1-30 days)
4. **Reset Configuration**: Admin-only option to restore default settings
5. **Exit**: Save data and exit program

### Admin Features
- **Password**: `kumarayush0104` (stored in admin.txt)
- **Reset Function**: Restores campus to default configuration
- **Data Protection**: Prevents unauthorized configuration changes

## Campus Data Structure

### Location Attributes
- **ID**: Unique identifier
- **Name**: Descriptive location name
- **Importance**: Priority level (1-10)
- **Cleaning Frequency**: Preferred days between cleanings
- **Visit Priority**: Base cleaning priority (1-10)
- **Cleanliness Status**: Current cleanliness percentage (0-100%)
- **Last Cleaned**: Days since last cleaning

### Path Attributes
- **From/To**: Connected locations
- **Distance**: Physical distance
- **Travel Time**: Estimated travel duration
- **Difficulty**: Road condition factor

## Simulation Features

### Daily Maintenance Routine
1. Update cleanliness status based on time elapsed
2. Calculate dynamic priorities for all locations
3. Select top-priority locations (approximately 1/3 of total)
4. Generate optimal route visiting selected locations
5. Mark visited locations as cleaned
6. Update visit counts and persistence data

### Output Format
```
=== Day X ===
Path: Library -> Classroom -> Cafeteria -> Library
Route Cost: 15.75

=== Campus Locations Status ===
Location                    Cleanliness    Last Cleaned        Priority      Visits
----------------------------------------------------------------------------------------
Library                         100.00 %           0 days         12.45          15
Classroom                        85.50 %           2 days         18.75           8
Cafeteria                        92.30 %           1 days         15.20          12
```

## Technical Details

### File Formats

**campus_data.txt**:
```
# Locations
0,Library,8,7,6,100.000000,0,0
1,Classroom,6,5,5,85.500000,2,8
2,Cafeteria,7,3,7,92.300000,1,12

# Paths
0,1,150.000000,2.500000,1.200000
0,2,200.000000,3.000000,1.500000
1,2,100.000000,1.500000,1.000000
```

**admin.txt**:
```
kumarayush0104
```

**visiting_frequency.txt**:
```
15 8 12 0 0 0 0
```

### Algorithm Complexity
- **Time Complexity**: O((V + E) log V) for Dijkstra's algorithm
- **Space Complexity**: O(V + E) for graph representation
- **Optimizations**: Priority queue implementation for efficient pathfinding

## Testing & Validation

### Test Scenarios
1. **Compilation**: Verify error-free compilation with g++
2. **Menu Navigation**: Test all menu options functionality
3. **Pathfinding**: Validate optimal route calculations
4. **File Operations**: Test save/load functionality
5. **Admin Features**: Verify password protection
6. **Simulation**: Run multi-day simulations for consistency

### Expected Output
- Clean compilation without warnings
- Accurate path calculations
- Proper data persistence
- Correct admin authentication
- Realistic simulation results

## Troubleshooting

### Common Issues
1. **File Not Found Errors**:
   - Ensure `campus_data.txt`, `admin.txt` are present
   - Check file permissions in executable directory

2. **Compilation Errors**:
   - Verify g++ installation: `g++ --version`
   - Ensure C++11 support: `g++ -std=c++11 Improved.cpp -o output.exe`

3. **Admin Access Denied**:
   - Check `admin.txt` contains correct password
   - Verify file encoding (should be plain text)

4. **Simulation Issues**:
   - Ensure campus_data.txt has valid format
   - Check for missing location or path definitions

### Performance Considerations
- Large graphs may require optimization
- Consider memory usage for very large campuses
- File I/O operations may impact performance on slow storage

## Future Enhancements

### Short-Term Goals
- [ ] Graphical user interface (GUI)
- [ ] Real-time visualization of maintenance routes
- [ ] Enhanced reporting and analytics
- [ ] Mobile application integration

### Long-Term Vision
- [ ] IoT sensor integration for real-time cleanliness monitoring
- [ ] Machine learning for predictive maintenance scheduling
- [ ] Multi-campus support and coordination
- [ ] Cloud-based data synchronization

## Contributing

We welcome contributions to enhance miniP! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Commit changes: `git commit -m 'Add feature'`
4. Push to branch: `git push origin feature-name`
5. Submit a pull request

### Code Standards
- Follow C++ best practices
- Include comments for complex logic
- Maintain consistent formatting
- Add tests for new features

## License

This project is currently unlicensed. Please contact the authors for usage permissions.

## Authors & Acknowledgments

### Core Development Team
- **Ayush Kumar**
- **Mithun Dutta**
- **Piyush Wadadare**
### Special Thanks
- **Professor Abhik Mukherjee** for guidance and support
- All team members for collaborative effort

### Technologies Used
- **C++11** with Standard Template Library (STL)
- **Modified Dijkstra's Algorithm**
- **File I/O Operations** for data persistence
- **Priority Queue** for efficient pathfinding

## Version History

- **v1.0** (Current): Initial release with core functionality
  - Basic campus management
  - Modified Dijkstra algorithm
  - File persistence
  - Admin features
  - Simulation capabilities

## Support

For questions, issues, or suggestions:
1. Check the troubleshooting section above
2. Review the code comments for implementation details
3. Contact the development team for assistance

---

*Making Campus Maintenance Smarter and More Efficient*
