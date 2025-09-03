#我的研究生 
# Conditional Probability
For any two events A and B with P(B)>0, the conditional probabiliity of *A given B* has occurred is defined by：$P(A|B)=\frac{P(A \cap B)}{P(B)}$
注意：哪个事件先发生，则作为分母以及放在“|”之后
## The Multiplication Rule：
1. $P(A \cap B) = P(A|B)P(B)$ 
2. $P(A \cap B) = P(B|A)P(A)$
### the general multiplication rule
$P(A \cap B \cap C)=P(A|B \cap C)P(B|C)P(C)$
## Theorem: Law of Total Probability
通过多个条件概率计算整个事件的概率，关键在于定义出确定的mutually exclusive and exhaustive事件
$P(B)=P(B|A)P(A)+P(B|A^\prime)P(A^\prime)$
#### Proof
$P(B)=P(A \cap B) + P(A^\prime \cap B)= P(B|A)P(A)+P(B|A^\prime)P(A^\prime)$
### General version:
Let A1, ... ,Ak be *mutually exclusive* and *exhaustive events*
$P(B)=P(B|A_1)P(A_1)+...+P(B|A_k)P(A_k)$
# Bayes' Theorem
Let $A_1$, ... ,$A_k$ be a collection of *mutually exclusive* and *exhaustive events* with $P(A_i)>0$ for i=1......k. Then for any other event B with $P(B)>0$,
$P(A_j|B)=\frac{P(B|A_j)P(A_j)}{\sum{P(B|A_i)P(A_i)}}$,  i , j=1,...,k
将求$P(A|B)$ 转换为求$P(B|A)$ 和$P(A)$
# Independence
Two Event A and B with $P(A)>0$ and $P(B)>0$ are independent if and only if:
- $P(A|B) = P(A)$ or $P(B|A)=P(B)$ or $P(A \cap B)=P(A)P(B)$

**The only way to identify that whether event A and B are independent or not is** : $P(A \cap B)= P(A)P(B)$
If A,B are independent, then:
A and $B^\prime$, $A^\prime$ and B, $A^\prime$ and $B^\prime$ are also independent

---
