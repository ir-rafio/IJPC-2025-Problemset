# Editorial for Intra-IUT Junior Programming Contest 2025

<details>
<summary>Problem A - Arcane Accumulation</summary>

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

<details>
<summary>Problem B - Balloon</summary>

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
<summary>Problem D - Arise</summary>

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
<summary>Problem F - Inverted Query</summary>

Problem Setter: [Mahiul Kabir](https://codeforces.com/profile/the-NerdNinja)

Difficulty: Easy-Medium

Tags: Range Query

<details>
<summary>**Hint 0** : How can you find the maximum absolute difference of 2 elements of any set?</summary>

The maximum difference can be found by taking the maximum and the minimum elements from the set.
Why? because if the elements were x, y; where x < y, taking a smaller element x' will always improve the result.

</details>

<details>
<summary>**Hint 1** : What are we left with when we remove range [l, r] form the array?</summary>

We have some prefix of the array, and some suffix.

</details>

<details>
<summary>Solution</summary>

Obviously, the brute force approach is too slow to pass the time limit.

From the Hints, we deduce that we need to find the maximum and the minimum elements of prefix[A_1 to A_(l-1)], and suffix[A_(r+1), A_n]. This can be done with the classic trick: **_prefix arrays_**.
We precompute 4 arrays,

- prefix min array
- prefix max array
- suffix min array
- suffix max array

and combine the results accordingly.

<details>
<summary>Code</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int n, q;
    cin >> n >> q;
    vector<int> A(n+2);
    for (int i = 1; i <= n; i++)
        cin >> A[i];

    const int INF = 1e9 + 5;
    vector<int> pref_min(n+2, INF), pref_max(n+2, -INF);
    vector<int> suff_min(n+2, INF), suff_max(n+2, -INF);

    // Build prefix
    for (int i = 1; i <= n; i++) {
        pref_min[i] = min(pref_min[i-1], A[i]);
        pref_max[i] = max(pref_max[i-1], A[i]);
    }
    // Build suffix
    for (int i = n; i >= 1; i--) {
        suff_min[i] = min(suff_min[i+1], A[i]);
        suff_max[i] = max(suff_max[i+1], A[i]);
    }

    while (q--) {
        int l, r;
        cin >> l >> r;

        int outside_min = INF, outside_max = -INF;
        int outside_count = 0;

        // prefix part [1..l-1]
        if (l > 1) {
            outside_min = min(outside_min, pref_min[l-1]);
            outside_max = max(outside_max, pref_max[l-1]);
            outside_count += (l-1);
        }
        // suffix part [r+1..n]
        if (r < n) {
            outside_min = min(outside_min, suff_min[r+1]);
            outside_max = max(outside_max, suff_max[r+1]);
            outside_count += (n - r);
        }

        if (outside_count < 2) {
            cout << -1 << "\n";
        } else {
            cout << (outside_max - outside_min) << "\n";
        }
    }
}

int main(){
  int tc; cin >> tc;
  while(tc--) solve();
}

```

</details>
</details>
</details>

<details>
<summary>Problem G - Trouble in the North</summary>

Problem Setter: [Abdullah Abrar](https://codeforces.com/profile/lelbaba)

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
<summary>Problem H - Hex Game</summary>

Problem Setter: [Rafio](https://codeforces.com/profile/Rafio)

Difficulty: Medium-Hard

Tags: Geometry, Interactive, Game Theory

<details>
<summary>Hint 1</summary>

You can't control what your opponent will do. So try to come up with a _simple_ strategy where you'll have a response for _anything_ your opponent does.

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
