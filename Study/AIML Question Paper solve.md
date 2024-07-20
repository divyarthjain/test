#### Question 1(a)

**Consider the driverless cars. The car may ply through both heavy-traffic and traffic-less areas. What are the PEAS components needed for it? Also explain, how do you estimate its performance?**

**PEAS Components for Driverless Cars:**

- **Performance Measure:** Safety (accidents avoided), passenger comfort, travel time, fuel efficiency, adherence to traffic rules.
- **Environment:** Urban streets, highways, traffic signals, pedestrians, other vehicles, varying weather conditions.
- **Actuators:** Steering wheel, accelerator, brake, indicators, horn, communication systems.
- **Sensors:** Cameras, LiDAR, radar, GPS, speed sensors, accelerometers.

**Estimating Performance:**

- **Simulation Tests:** Running the car in simulated environments to test response to various scenarios.
- **Field Tests:** Real-world testing in controlled environments and public roads.
- **Safety Records:** Tracking accidents and near-misses.
- **Passenger Feedback:** Comfort and satisfaction surveys.
- **Compliance with Traffic Laws:** Monitoring adherence to legal requirements.

#### Question 1(b)

**Is it rational for the agent to oscillate needlessly back and forth after all the dirt is cleaned up? Why? How might a vacuum-cleaner agent adapt its behavior in an environment where clean squares can become dirty again?**

- **Rationality of Oscillation:** No, it is not rational. Oscillation wastes energy and reduces the lifespan of the vacuum-cleaner without providing any benefit.
- **Adaptive Behavior:**
    - **Persistent Checking:** The agent can periodically recheck previously cleaned areas.
    - **Dynamic Path Planning:** Adjust cleaning patterns based on the likelihood of dirt accumulation in specific areas.
    - **Learning from Experience:** Using past data to predict and prioritize areas that get dirty frequently.


### Question 2(a)

**Develop an algorithm for a 3x3 game board for a simple two-player Tic-Tac-Toe game.**

To develop an algorithm for a 3x3 Tic-Tac-Toe game, follow these steps:

1. **Initialize the Game Board:**
    
    - Create a 3x3 grid, which can be represented as a 2D array or matrix.
    - Each cell in the grid starts as empty (denoted by a blank space or some initial value).
2. **Define Players:**
    
    - Assign symbols to the two players, typically 'X' and 'O'.
3. **Set Up the Game Loop:**
    
    - The game loop continues until there is a winner or all cells are filled (a draw).
4. **Player Move:**
    
    - Prompt the current player to choose a cell by specifying the row and column.
    - Validate the move to ensure the chosen cell is empty. If not, ask the player to choose another cell.
5. **Update the Board:**
    
    - Place the current player's symbol ('X' or 'O') in the chosen cell.
6. **Check for a Winner:**
    
    - After each move, check if the current player has won by forming a straight line of three of their symbols.
    - Check horizontally, vertically, and diagonally for a line of three identical symbols.
    - If a player wins, declare the winner and end the game loop.
7. **Switch Player:**
    
    - Alternate between the two players after each move.
8. **Check for a Draw:**
    
    - If all cells are filled and there is no winner, declare the game as a draw.
9. **End the Game:**
    
    - Display the final board state.
    - Announce the winner or declare a draw.


### Question 2(b)

**Draw the state space diagram for the Hill Climbing Search and explain several regions of it.**

Hill Climbing is a heuristic search algorithm used for mathematical optimization problems. The algorithm starts with an arbitrary solution and iteratively makes incremental changes to the solution, attempting to find a better one. If the change produces a better solution, the new solution becomes the current solution. This process is repeated until no further improvements can be found

      S7
      |
      |
      S6
      |
      |
      S5
     / \
	S4   S3
    |
    |
	S2
    |
    |
	S1 (initial state)

**Regions Explanation:**

1. **Initial State (S1):**
    
    - This is the starting point of the search.
2. **Ascending States (S2, S4, S6, S7):**
    
    - These states represent an ascent towards a higher value (or lower cost).
    - Each move improves the current state.
3. **Local Maximum (S7):**
    
    - The highest point in the immediate neighborhood.
    - No neighboring state has a higher value, so the algorithm stops here.
4. **Plateaus (not shown in this simple diagram):**
    
    - Flat areas where neighboring states have the same value.
    - The algorithm can get stuck in these regions, moving randomly without making progress.
5. **Ridges (not shown in this simple diagram):**
    
    - Narrow peaks extending higher.
    - The algorithm might need specific moves to ascend properly.
6. **Global Maximum (if the diagram extended beyond S7):**
    
    - The highest point in the entire state space.
    - Ideally, Hill Climbing should find this, but it can get stuck at local maxima instead.
### Steps in Words:

1. **Start at Initial State (S1):**
    
    - Evaluate the neighboring states (S2).
2. **Move to State with Higher Value (S2):**
    
    - Evaluate its neighbors (S4).
3. **Continue Moving Upwards (S4 to S5):**
    
    - Always choose the state with a higher value.
4. **Reach Local Maximum (S7):**
    
    - When no neighbor offers a higher value, stop the algorithm.


### Question 3(a)

**Discuss the role of unification in First Order Predicate Logic. Provide examples to illustrate how unification is applied when resolving variables in different clauses.**

#### Role of Unification

Unification in First Order Predicate Logic is a process used to determine if there exists a substitution that can make different logical expressions identical. It is crucial for automated reasoning systems, such as Prolog, as it enables the system to match patterns, resolve queries, and infer new information by combining known facts and rules.

#### Example

Consider the following two predicates:

1. `knows(John, X)`
2. `knows(Y, Mary)`

We want to unify these predicates to determine if there is a common ground.

#### Steps for Unification

1. **Match Predicate Names**:
    
    - Both predicates are `knows`, so we proceed to match their arguments.
2. **Match Arguments**:
    
    - The first argument in `knows(John, X)` is `John`.
    - The first argument in `knows(Y, Mary)` is `Y`.
    - We can unify `Y` with `John` (i.e., `Y = John`).
3. **Match Second Arguments**:
    
    - The second argument in `knows(John, X)` is `X`.
    - The second argument in `knows(Y, Mary)` is `Mary`.
    - We can unify `X` with `Mary` (i.e., `X = Mary`).

#### Resulting Substitution

By applying these substitutions, the two predicates become identical:

- `knows(John, X)` with `X = Mary` becomes `knows(John, Mary)`.
- `knows(Y, Mary)` with `Y = John` becomes `knows(John, Mary)`.

Hence, the unification is successful with the substitutions `Y = John` and `X = Mary`.


### Question 3(b)

**Create a Prolog program demonstrating backward chaining with a knowledge base related to the courses and prerequisites of a B.Tech. student at VIT Bhopal University.**

#### Knowledge Base

We will use the following simple courses and prerequisites:

- `course(cse101, "Introduction to Computer Science").`
- `course(cse102, "Data Structures").`
- `course(cse201, "Algorithms").`

Prerequisites:

- `prerequisite(cse102, cse101).`
- `prerequisite(cse201, cse102).`

#### Prolog Program

% Facts: Course information
course(cse101, "Introduction to Computer Science").
course(cse102, "Data Structures").
course(cse201, "Algorithms").

% Facts: Prerequisites
prerequisite(cse102, cse101).
prerequisite(cse201, cse102).

% Rule: Check if a course can be taken
can_take(Student, Course) :-
    \+ (prerequisite(Course, Prerequisite), \+ completed(Student, Prerequisite)).

% Facts: Completed courses by students
completed(student1, cse101).
completed(student1, cse102).

### Question 4(a)

**A road map can be represented as a set of facts:**

`road(City1, City2, Distance)`

**This predicate means that there is a direct road between the cities City1 and City2.**

Given the following facts:

`road(zurich, baden, 22). road(baden, basel, 83). road(zurich, rotkreuz, 39). road(baden, olten, 43). road(olten, bern, 67). road(olten, luzern, 57). road(olten, basel, 39). road(rotkreuz, luzern, 18). road(rotkreuz, schwyz, 26). road(luzern, altdorf, 39). road(schwyz, altdorf, 16).`

**Implement the predicate:**


`route(X, Y, W, L)`

**Hint: This predicate means that there is a route W from X to Y of length L. W is the ordered list of the cities in between, starting with X.**

### Explanation:

To solve this problem, we'll use Prolog to find a route between two cities, X and Y, with the route represented as an ordered list of cities W and the total length of the route L.

#### Steps:

1. **Define the Facts:**
    
    - The given facts about the roads between cities and their distances.
2. **Define the Base Case:**
    
    - A direct route between two cities.
3. **Define the Recursive Case:**
    
    - Find an intermediate city that connects the current city to the destination.
4. **Accumulate the Route and Distance:**
    
    - Keep track of the cities visited and the total distance traveled.

### Example in Words:

1. **Base Case:**
    
    - If there's a direct road between two cities, return the route and the distance.
2. **Recursive Case:**
    
    - For a route from X to Y:
        - Find a city Z such that there is a road from X to Z.
        - Recursively find a route from Z to Y.
        - Combine the route from X to Z with the route from Z to Y.
        - Sum the distances of these routes.

### Prolog Program (Simplified Explanation):

1. **Facts:**
    
    - Define the direct roads with distances.
2. **Base Case:**
    
    - If there is a direct road from X to Y, the route is `[X, Y]` and the distance is the distance of that road.
3. **Recursive Case:**
    
    - If there is no direct road from X to Y, find a city Z such that there is a road from X to Z and a route from Z to Y.
    - Combine the route and distances appropriately.

Here’s the simplified explanation without using code, using an example:

### Example Route Calculation:

**Finding a Route from Zurich to Luzern:**

1. **Base Case:**
    
    - Check for a direct road from Zurich to Luzern.
    - No direct road exists.
2. **Recursive Case:**
    
    - Check for intermediate cities:
        - Road from Zurich to Rotkreuz (Distance: 39).
        - From Rotkreuz, find a route to Luzern.
        - Road from Rotkreuz to Luzern (Distance: 18).
    - Combine the routes:
        - Route: `[Zurich, Rotkreuz, Luzern]`
        - Total Distance: `39 + 18 = 57`.

Thus, the route from Zurich to Luzern is `[Zurich, Rotkreuz, Luzern]` with a total distance of 57.

This approach illustrates how backward chaining and recursive logic can be used in Prolog to find routes in a road map.