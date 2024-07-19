## **Shapley Value Problem**

You are given a cooperative game defined by a characteristic function `v` that assigns a value to each coalition of players. Write a function to compute the Shapley value for each player. The Shapley value is the average marginal contribution of a player across all possible coalitions.

The Shapley value of a player `i` in a cooperative game with a characteristic function `v` and `N` players is given by:

$$
\Phi_i(v) = \sum_{S \subseteq N\backslash\{i\}} \frac{|S|!(|N|-|S|-1)!}{|N|!} \cdot (v(S \cup \{i\}) - v(S))
$$

where:

- $\Phi_i(v)$: Shapley value of player $i$ in a cooperative game with characteristic function $v$.
- $\sum_{S \subseteq N\backslash\{i\}}$: Summation over all coalitions $S$ that do not include player $i$.
- $\frac{|S|!(|N|-|S|-1)!}{|N|!}$: The number of orders in which the players can form a coalition that results in $S$ being formed before $i$ joins.
- $v(S \cup \{i\})$: Value of the coalition formed by adding player $i$ to coalition $S$.
- $v(S)$: Value of coalition $S$ without player $i$.

#### **Sample Input 1**

    v = {(): 0, ('A',): 1, ('B',): 2, ('A', 'B'): 4}

#### **Sample Output 1**

    {'A': 1.5, 'B': 2.5}

#### **Sample Explanation 1**

In this sample input, there are 2 possible order in which players can form a coalition.

{} -> 'A' -> 'B'		(1)

{} -> 'B' -> 'A'.	(2)

The marginal contribution in scenario (1) of 'A' is represented by {} -> 'A' which is 1, while the marginal contribution of 'A' in scenario (2) is represented by 'B' -> 'BA' which is 2.

So the shapely value of the 'A' is (2+1)/2 = 1.5.

#### **Sample Input 2**

    v = {(): 0, ('A', ): 24, ('B', ): 13, ('C', ): 11, ('A', 'B'): 50, ('A', 'C'): 35, ('B', 'C'): 30, ('A', 'B', 'C'): 100}

#### **Sample Output 2**

    {'A': 41.5, 'B': 33.5, 'C': 25.0}

#### **Expected Time Complexity**

__O__(n!), where n is the number of players.

#### **Expected Space Complexity**

__O__(n), where n is the number of players.

#### **Constraints**

    1 <= len(v) <= 20
    Values assigned by the characteristic function are integers.
