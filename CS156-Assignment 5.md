# Q 1:
The idea behind simulated annealing is try to give a momentum to each step to see whether it's in the local maximum or minimum. It start at a high "temperature", and then gradually reduce the intensity of temperature(search size and frequency). It picks a random move, and check if it improves the situation. If it does, the solution is always accepted, but if it doesn't, it will move with some probability less than 1. The probability is decreasing with the "badness" of the move (represented by ΔE) and with the temperature goes down. The pseudo code is like this:
```
Function Simulated-Annealing(problem, schedule) return a solution state
	input problem, schedule: a mapping from time to temperature
	variables: current, current node; next: the next node; T: a temperature controlling 

	current <-- Make-Node(initial-state[problem])
	for t from 1 to infinity
		T = schedule[t]
		if T=0 then return current
		next = a randomly selected successor of current
		ΔE = Value[next]-Value[current]
		if ΔE >0 then current = next
		else current = next only with probability e^(ΔE/T)
```

# Q 2:
They are different in state choosing. K-beam search choose the best k from the pool of candidate successors each time. However, the GA generate the successor states by combing 2 parent states.

# Q 3:
Variables: $X_{ij}$ = the blank of i * j (i: row, j: column)
Domains $D_{1}$ = {1,2,3,4,5,6,7,8,9}
Constrains:
- $1\leq i\leq 9$, $1\leq j\leq 9$
- For any single rows and column,  X needs involve number 1 to 9 and each number only shows once
- For each 3 * 3 box， $X$ needs involve number 1 to 9 and each number only shows once
- There are some given numbers for come blank $X_{ij}$

# Q 4:
The pseudo code for AC 3 is below:
```
function AC-3(csp) returns false if an inconsistency is found and true otherwise
	inputs: csp, a binary CSP with components (X, D, C)
	local variables: queue, a queue of arcs, initially all the arcs in csp

	while queue is not empty do
		(Xi, Xj) = REMOVE-FIRST(queue)
			if REVISE(csp, Xi, Xj ) then
				if size of Di == 0
					then return false
				for each Xk in Xi.NEIGHBORS - {Xj} do
					add (Xk, Xi) to queue
	return true

function REVISE(csp, Xi, Xj ) returns true if we revise the domain of Xi
	revised = false
	for each x in Di do
		if no value y in Dj allows (x ,y) to satisfy the constraint between Xi and Xj then
			delete x from Di
			revised = true
		return revised
```
In the REVISE function, if we find $D_{i}$ become smaller, we add $(X_{k},X_{i})$ to the queue. But if $D_{i}$ become nothing, we can know that the whole CSP has no consistent solution. Therefore we detect failures early.