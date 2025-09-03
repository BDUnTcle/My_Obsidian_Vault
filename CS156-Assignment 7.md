---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---
# Q 1
In the Monte Carlo Tree search , multiple simulations are keep going and in each iteration, it choose node and expand the node by certain strategy (UCT is one of them). And after simulate and get the result, it  uses back propagation to modify the path in each iteration. Usually it records the times for each node be selected in all simulation.
```
Function Monte-Carlo-TreeSearch(state) return action
	tree <- Node(state)
	while is-terminate() do
		leaf <- select(tree)
		child <- expand(leaf)
		result <- simulate(child)
		back-propagate(result)
	return the move in state whose node has the most playouts
```
The UCT is a policy in the search to effectively choose the child. In the formular
$$
UCB(n)=\frac{U(n)}{N(n)}+C\sqrt{ \frac{\log{N(Parent(n))}}{N(n)} }
$$
The U (n) is  total utility of all playouts go through the node n, N (n) is the number of playouts through node n, Parent (n) is the parent node of n in the tree.

# Q 2
Build the truth table for Food, Drinks and Party:

| Food | Drinks | Party | Food => Party | Drinks => Party | (Food => Party) v (Drinks => Party) | (Food ^ Drinks) | (Food ^ Drinks) => Party | Statement |
| ---- | ------ | ----- | ------------- | --------------- | ----------------------------------- | --------------- | ------------------------ | --------- |
| T    | T      | T     | T             | T               | T                                   | T               | T                        | T         |
| T    | T      | F     | F             | F               | F                                   | T               | F                        | T         |
| T    | F      | T     | T             | T               | T                                   | F               | T                        | T         |
| T    | F      | F     | F             | T               | T                                   | F               | T                        | T         |
| F    | T      | T     | T             | T               | T                                   | F               | T                        | T         |
| F    | T      | F     | T             | F               | T                                   | F               | T                        | T         |
| F    | F      | T     | T             | T               | T                                   | F               | T                        | T         |
| F    | F      | F     | T             | T               | T                                   | F               | T                        | T         |

A): From the table we know that the statement is true for all values
B):
Step 1: Left-Hand Side: $(\text{Food} \Rightarrow \text{Party}) \vee (\text{Drinks} \Rightarrow \text{Party})$
1. Food⇒Party is equivalent to $\neg \text{Food} \vee \text{Party}$
2. Drinks⇒Party is equivalent to $\neg \text{Drinks} \vee \text{Party}$
3. get (¬Food∨Party)∨(¬Drinks∨Party)
4. simplify it get (¬Food∨¬Drinks∨Party)

Step 2：right-Hand Slide: (Food∧Drinks)⇒Party
1. (Food∧Drinks)⇒Party is equivalent to $\neg (\text{Food} \land \text{Drinks}) \vee \text{Party}$
2. ¬(Food∧Drinks) is equivalent to $\neg \text{Food} \vee \neg \text{Drinks}$
3. So, the right-hand side in CNF is $(\neg \text{Food} \vee \neg \text{Drinks} \vee \text{Party})$
Because left side is same as right side, which means the sentence is always true.

C): The negation of the sentence is :
¬((¬Food∨¬Drinks∨Party)⇒(¬Food∨¬Drinks∨Party)), which can be simplified to (¬Food∨¬Drinks∨Party) is false
So the original sentence is true.

# Q3
The correct proposals are : b, d, e, g, h, i

# Q 4
In (A∨B) ∧(¬A∨C) ∧(¬B∨D) ∧(¬C∨G) ∧(¬D∨G), assuming that we have negation of G: ¬G
1. Resolving ¬G with (¬C∨G). We get ¬C
2. Resolving ¬C with (¬A∨C). We get ¬A
3. Resolving ¬A with (A∨B). We get B
4. Resolving B with ¬B∨D. We get D
5. Resolving D with ¬D∨¬G. We get G
Because there is contradiction so the original CNF entails G.