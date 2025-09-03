# Q 1
## Tree without ordering
![[Pasted image 20241021180949.png]]
During the α-β pruning algorithm,
First, explore $a_{1}$  to $b_{1}$ $b_{2}$ $b_{3}$ get Node B=4, $\alpha=4$
Then explore $a_{2}$ $c_{1}$ because 1 < 4 so this branch is pruned
Next explore $a_{3}$ $d_{1}$, also 3 < 4, so this branch is also be pruned
Finally get the Node A = 4
Because only half of nodes was looked through the algorithm, the time complexity is $O(b^{m/2})$, here b=3. m=9
## Tree with perfect ordering
![[Pasted image 20241021181432.png]]
For this tree, the  α-β pruning algorithm needs to go through all nodes for all branches and nothing is pruned.
All the nodes are looked through the algorithm, the time complexity becomes $O(b^{m})$, here b=3. m=9
# Q 2
In the games with chances (Non-deterministic), we need to add a chance layer between max and min which means the probability of choosing which successor.
In the algorithm with chance, we calculate the minmax value by highest expected value (adding all successor's value time it probability) for max and lowest expected value for min.