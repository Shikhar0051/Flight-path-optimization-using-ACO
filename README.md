## Flight Path Optimization using Ant Colony Optimization

### Introduction
##### Ant Colony Optimization
Ant colony optimization (ACO) is a meta-heuristic technique in the field of swarm intelligence. It is use for solving different combinatorial optimization problems.

ACO is based on the behaviors of ant colony and their  search capability for combinatorial optimization. Analysis of natural behavior of ant colonies show that the ants move along the rich pheromone distribution on their path. The algorithm imitates this behavior.

##### Flight Path Optimization Problem
The Flight Path Optimization is a problem focused on optimization and providing a optimized path solution.

> A better solution often means a solution that is cheaper, shorter, or faster.


### Dataset
The dataset consists of 225 cities in the North-West and Central part of the Indian sub continent.

##### Dataset structure
```
tsp dataset/
    ├── distance.txt
    ├── location_ll.txt
    ├── location_map.jpg
    ├── location_map_satellite_image.jpg
    ├── names.txt
    ├── road_distance.txt
    └── travel_time.txt
```

##### File description
|      **File**     |                            **Description**                           |
|:-----------------:|:--------------------------------------------------------------------:|
|  location_ll.txt  | Space separated Geo locations (latitude and longitude) of each city. |
|    distance.txt   | Eucledian distance between the cities.                               |
| road_distance.txt | Distance by road between the cities.                                 |
|  travel_time.txt  | Time take to travel from one city to another.                        |

### Algorithms
##### Ant Colony System
In Ant Colony System (ACS), a number of artificial ants are initially placed at random nodes. Each ant builds a tour. It chooses the next city by applying a *state transition rule* (greedy rule). This rule provides a balance between exploration of new edges and exploitation of accumulated knowledge.

> A constant amount of pheromone is deposited by each ant at each step on the most favorable route (best tour)

##### Elitist
Using the Elitist approach, we try to control the learning parameters. The ants that find the best route (quality) are rewarded more that the other ants. More pheromone is deposited on better routes, giving importance to that particular tour and reducing the time to get an optimal solution.

> The amount of pheromone deposited in based on the quality of the route. 

##### MaxMin
The MaxMin method aims to get the best of both worlds, a close to optimal solution with a quick execution time. This is achieved by varying the amount to pheromone deposited through the steps. 

Initially the weight is high, giving a quick learning rate. The weight gradually decreases till 75% completion. Then the model if fine tuned by applying weights by comparing the results to the *global best tour*.

At the end of each step, the weights are bound within the max and min pheromone limits to prevent the solution to running astray.

> The amount of pheromone gradually decreases for the first 75% of iterations. Then amount depends on the quality compared to the best tour.

##### Parameters

```py
params = {
    '_colony_size': "number of ants in the colony"  (default = 15),
    '_steps': "iteration to run through" (default = 50),
    '_mode': "mode of algorithm to run the model"
}
```

### Conclusion
With the help of ACO, we generate an optical path to cover all the cities while trying to minimize the travel distance. It is also found that lower the number of ants, faster an individual can change the path rather the higher number of ants, there is higher accumulation of pheromones on the edges causing individual to hold to the path. The greater advantage of ACO algorithm is that it provides relatively better results than other algorithms in less iterations.
