# Editorial for Intra-IUT Junior Programming Contest 2025

<details>
<summary>Problem A - Gotta Catch'Em All</summary>

Problem Setter: [Rafio](https://codeforces.com/profile/Rafio)

Difficulty: Medium

Tags: Combinatorics, Number Theory

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem B - Inverted Query</summary>

Problem Setter: [Mahiul Kabir](https://codeforces.com/profile/the-NerdNinja)

Difficulty: Easy-Medium

Tags: Range Query

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem C - You Can't See Me</summary>

Problem Setter: [Sabbir Ahmed](https://cse.iutoic-dhaka.edu/profile/sabbir/)

Difficulty: Easy

Tags: Math

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem D - Giveaway Problem</summary>

Problem Setter: [Reaz Hassan Joarder](https://codeforces.com/profile/ssshanto)

Difficulty: Giveaway

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem E - Eid Salami</summary>

Problem Setter: [Rafio](https://codeforces.com/profile/Rafio)

Difficulty: Hard

Tags: Greedy, Binary Search

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem F - Arise</summary>

Problem Setter: [Akib Haider](https://codeforces.com/profile/_akibhaider_)

Difficulty: Medium

Tags: Brute Force, Implementation, Strings

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>

<details>
<summary>Alternate Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem G1 - Maximum Expectations (Easy Version)</summary>

Problem Setter: [Rafio](https://codeforces.com/profile/Rafio)

Difficulty: Easy-Medium

Tags: Probability, DP, Math

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem G2 - Maximum Expectations (Hard Version)</summary>

Problem Setter: [Rafio](https://codeforces.com/profile/Rafio)

Difficulty: Medium

Tags: Probability, Math

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem H - Hex Game</summary>

Problem Setter: [Rafio](https://codeforces.com/profile/Rafio)

Difficulty: Medium-Hard

Tags: Geometry, Interactive, Game Theory

<details>
<summary>Hint 1</summary>

Try to come up with a simple strategy where you'll have a response for _anything_ your opponent does.

</details>

<details>
<summary>Hint 2</summary>

Solve a simpler problem. Ignore the hexagon and assume you can place disks anywhere. Try to come up with a strategy for a square or a circular board and make modifications to transfer the strategy for the hexagon.

</details>

<details>
<summary>Solution</summary>

The board is a _regular_ hexagon, which means it must be symmetric about its center. So, every point inside it must have a reflection through the center. The only exception is the center itself, which is its own reflection.

With that information, you can develop a strategy like this:

- Place the first disk in the center $C(0, l)$.
- Then, for every move the opponent makes at $P(x, y)$, respond with its reflection through the center: $P'(x', y')$.

Now,  
Vector $\vec{CP} = P - C = (x, y) - (0, l) = (x, y - l)$  
So, reflected vector $\vec{CP'} = -\vec{CP} = (-x, l - y)$  
So, the reflection point $P' = C + \vec{CP'} = (-x, 2l - y)$

<details>
<summary>Proof</summary>

- $C(0, l)$ is a lattice point.
- Since $r \le l/2$, the first disk easily fits inside the board, so your first move is valid.
- After you make the first move, the board remains symmetric.
- The center is now occupied, so your opponent cannot touch it.
- Before your opponent makes any move, the board is symmetric. So, if any point $P(x, y)$ is within the hexagon and not overlapping with any disk, the same applies to its reflection $P'(-x, 2l - y)$.
- So, if your opponent makes a valid move at $P$, your move at $P'$ will also be valid.
- Each time you respond to your opponent's move by mirroring it, _the board becomes symmetric again._ So, the property holds and you will always have the guarantee that **whenever your opponent makes a valid move, you have a valid response to that**.
- Eventually, your opponent will be forced to make an invalid move and you win!

</details>

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>

<details>
<summary>Problem I - The Wizards' Gambit</summary>

Problem Setter: [Jannatul Fardus Rakhi](https://codeforces.com/profile/sectumsemprra)

Difficulty: Medium

Tags: Greedy

<details>
<summary>Hint</summary>

Hint

</details>

<details>
<summary>Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
// Code
```

</details>
</details>
</details>
