1.
a):
- Initial State: Every boxes are locked, and you have the key for the first box.
- Goal State: Get the fruit
- Action Function：$S(x)$ is open the box with its key
- Cost Function：1 key per box

b):
- Initial State: Every square is unpainted, you are in the (x, y)
- Goal State: whole floor painted
- Action Function：$S(x)$ : paint the square(x, y) or move to the next unpainted adjacent square. 
- Cost Function：1 square for each

c):
- Initial State: all containers stay and the crane is above one.
- Goal State: all containers are unloaded
- Action Function：$S(x)$ : move to (x, y) and unload it
- Cost Function：1 container per step

2.
a): 
The state space can be the 1 of 4 direction and the number of step 
- Initial State: the middle coordinate for the maze
- Goal State: get to coordinate of the exit 
- Action Function: move n steps towards direction k
- Cost function: n steps per move
b):
In this constraint, the state space will be the n step or turn direction
- Initial State: the middle coordinate for the maze
- Goal State: get to coordinate of the exit 
- Action Function: move n steps straight, and turn a direction if encounter intersection
- Cost function: n steps per move or turn

c):
- Initial State: the middle coordinate for the maze
- Goal State: get to coordinate of the exit 
- Action Function: move n steps straight until get into a turning point, then turn into a direction
- Cost function: n steps per move
In this situation, we don't need to trace the orientation, because we don't care each direction the robot gets. We just keep go until get to the exit.

d):
1. We simplify the real maze environment into coordinate in a plane
2. We simplify the process of traveling the maze into steps and directions
3. We ignore the other factors the robot could encounter 