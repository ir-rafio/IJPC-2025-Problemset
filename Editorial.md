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
#include <bits/stdc++.h>
using namespace std;
#define ll long long


int main() {

          ios::sync_with_stdio(0);
          cin.tie(0);

          ll t=1,i,j;
          cin >> t;
         while(t--)
               {
                 ll n,k,sum = 0;
                 cin >> n >> k;
                 vector <ll> v(n);

                 for(i=0;i<n;i++){
                    cin >> v[i];
                    sum+= v[i];
                 }

                 vector <ll> pre(n,0);
                 pre[0] = v[0];

                 for (i=1;i<n;i++){
                    pre[i] = pre[i-1] + v[i];
                 }
                 ll mx_net_gain = 0;

                 for (i=0;i<n;i++){
                    mx_net_gain = max(mx_net_gain,pre[i]-v[i]);
                 }

                 ll ans = k*(mx_net_gain) + sum ;

                 cout << ans << endl;
               }

    return 0;
}
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

This problem has no input.

</details>

<details>
<summary>Solution</summary>

You can implement the decryption algorithm. But since the answer is fixed, it is easier to decrypt by yourself and then simply print the decrypted string.

<details>
<summary>Code</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    cout << "GIVE ME A BALLOON";
}
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
#include <bits/stdc++.h>
using namespace std;

#define fastio ios_base::sync_with_stdio(0); cin.tie(0)

using LL = long long;



void pre()
{
    fastio;


}

void solve(int tc)
{
    int i, n;
    cin >> n;

    vector<int> k(n);
    for(auto &it: k) cin >> it;

    LL d = 0;
    for(i = 0; i < n; i++) d += k[i] - 1;

    cout << d + 1;
}

signed main()
{
    pre();

    int tc, tt = 1;
    cin >> tt;

    for(tc = 1; tc <= tt; tc++)
    {
        // cout << "Case " << tc << ": ";
        solve(tc);
        cout << endl;
    }

    return 0;
}
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
#include <bits/stdc++.h>
using namespace std;

#define fastio ios_base::sync_with_stdio(0); cin.tie(0)
using LL = long long;

bool foundInLine(vector<string>& grid, string& str, int sx, int sy, int dx, int dy)
{
    int k, l = str.size(), n = grid.size(), m = grid[0].size();
    int x, y, kx, ky;

    for(k = 0; k < l; k++)
    {
        kx = k * dx;
        ky = k * dy;

        x = sx + kx;
        y = sy + ky;

        if(x < 0) return 0;
        if(y < 0) return 0;

        if(x >= n) return 0;
        if(y >= m) return 0;

        if(grid[x][y] != str[k]) return 0;
    }

    return 1;
}

bool foundInGrid(vector<string>& grid, string& str)
{
    int i, j, n = grid.size(), m = grid[0].size();

    for(i = 0; i < n; i++)
    {
        for(j = 0; j < m; j++)
        {
            if(foundInLine(grid, str, i, j, 1, 0)) return 1;
            if(foundInLine(grid, str, i, j, -1, 0)) return 1;
            if(foundInLine(grid, str, i, j, 0, 1)) return 1;
            if(foundInLine(grid, str, i, j, 0, -1)) return 1;
            if(foundInLine(grid, str, i, j, 1, 1)) return 1;
            if(foundInLine(grid, str, i, j, 1, -1)) return 1;
            if(foundInLine(grid, str, i, j, -1, 1)) return 1;
            if(foundInLine(grid, str, i, j, -1, -1)) return 1;
        }
    }

    return 0;
}



void pre()
{
    fastio;


}

void solve(int tc)
{
    int n, m;
    cin >> n >> m;

    vector<string> grid(n);
    for(auto &row: grid) cin >> row;

    int f, cnt = 0;
    string str;
    cin >> f;

    while(f--)
    {
        cin >> str;
        cnt += foundInGrid(grid, str);
    }

    cout << cnt;
}

int main()
{
    pre();

    int tc, tt = 1;
    cin >> tt;

    for(tc = 1; tc <= tt; tc++)
    {
        solve(tc);
        cout << '\n';
    }

    return 0;
}
```

</details>
</details>

<details>
<summary>Alternate Solution</summary>

Solution

<details>
<summary>Code</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

#define fastio ios_base::sync_with_stdio(0); cin.tie(0)
using LL = long long;

void gridToText(vector<string>& grid, string& text)
{
    int i, j, k, n = grid.size(), m = grid[0].size();
    char sep = ' ';

    // Left to Right
    for(i = 0; i < n; i++)
    {
        for(j = 0; j < m; j++)
        {
            text.push_back(grid[i][j]);
        }

        text.push_back(sep);
    }

    // Top to Bottom
    for(j = 0; j < m; j++)
    {
        for(i = 0; i < n; i++)
        {
            text.push_back(grid[i][j]);
        }

        text.push_back(sep);
    }

    // Top-Left to Bottom-Right
    for(i = 0; i < n; i++)
    {
        for(k = 0; i + k < n && k < m; k++)
        {
            text.push_back(grid[i + k][k]);
        }

        text.push_back(sep);
    }
    for(j = 1; j < m; j++)
    {
        for(k = 0; k < n && j + k < m; k++)
        {
            text.push_back(grid[k][j + k]);
        }

        text.push_back(sep);
    }

    // Bottom-Left to Top-Right
    for(i = 0; i < n; i++)
    {
        for(k = 0; i - k >= 0 && k < m; k++)
        {
            text.push_back(grid[i - k][k]);
        }

        text.push_back(sep);
    }
    for(j = 1; j < m; j++)
    {
        for(k = 0; k < n && j + k < m; k++)
        {
            text.push_back(grid[n - 1 - k][j + k]);
        }

        text.push_back(sep);
    }

    string rev = text;
    rev.pop_back(); // remove last sep
    reverse(rev.begin(), rev.end());
    text = text + rev;
}

bool foundInText(string& text, string& pattern)
{
    int i, j, n = text.size(), m = pattern.size();
    string window;

    for(i = 0; i < n; i++)
    {
        window = text.substr(i, m);
        if(window == pattern) return 1;
    }

    return 0;
}


void pre()
{
    fastio;


}

void solve(int tc)
{
    int n, m;
    cin >> n >> m;

    vector<string> grid(n);
    for(auto &row: grid) cin >> row;

    string text, soldier;
    gridToText(grid, text);

    // Check out how the text looks
    // cout << text << '\n';

    int i, q, cnt = 0;
    cin >> q;

    for(i = 0; i < q; i++)
    {
        cin >> soldier;
        cnt += foundInText(text, soldier);
    }

    cout << cnt;
}

int main()
{
    pre();

    int tc, tt = 1;
    cin >> tt;

    for(tc = 1; tc <= tt; tc++)
    {
        solve(tc);
        cout << '\n';
    }

    return 0;
}
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
#include <bits/stdc++.h>
using namespace std;

#define fastio ios_base::sync_with_stdio(0); cin.tie(0)

using LL = long long;

bool comp(pair<int,int> p1, pair<int,int> p2)
{
    auto [g1, r1] = p1; // g1 = p1.first; r1 = p1.second;
    auto [g2, r2] = p2;

    int delta1 = r1 - g1, delta2 = r2 - g2;

    if(delta1 > 0 && delta2 > 0) return g1 < g2; // Sort delta-positive houses by ascending order of giving amount
    if(delta1 <= 0 && delta2 <= 0) return r1 > r2; // Sort delta-negative houses by descending order of receiving amount
    return delta1 > delta2; // Visit delta-positive houses before delta-negative houses
}



void pre()
{
    fastio;


}

void solve(int tc)
{
    int i, n;
    cin >> n;

    vector<pair<int,int>> v(n);
    for(auto &it: v) cin >> it.first; // for(i = 0; i < n; i++) cin >> v[i].first;
    for(auto &it: v) cin >> it.second;

    sort(v.begin(), v.end(), comp);

    int give, receive;
    LL balance = 0, ans = 0;

    for(auto it: v)
    {
        give = it.first;
        receive = it.second;

        balance -= give;

        ans = max(ans, -balance);

        balance += receive;
    }

    cout << ans;
}

signed main()
{
    pre();

    int tc, tt = 1;
    cin >> tt;

    for(tc = 1; tc <= tt; tc++)
    {
        // cout << "Case " << tc << ": ";
        solve(tc);
        cout << endl;
    }

    return 0;
}
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
#include <bits/stdc++.h>
using namespace std;

#define fastio ios_base::sync_with_stdio(0); cin.tie(0)
using LL = long long;



void pre()
{
    fastio;


}

void solve(int tc)
{
    int a, b, c, d;
    cin >> a >> b >> c >> d;

    int sum = a + b + c + d;
    cout << sum - 3 * a << ' ' << sum - 3 * b << ' ' << sum - 3 * c << ' ' << sum - 3 * d;
}

signed main()
{
    pre();

    int tc, tt = 1;
    cin >> tt;

    for(tc = 1; tc <= tt; tc++)
    {
        // cout << "Case " << tc << ": ";
        solve(tc);
        cout << '\n';
    }

    return 0;
}
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
#include <bits/stdc++.h>
using namespace std;

#define fastio ios_base::sync_with_stdio(0); cin.tie(0)
using LL = long long;



void pre()
{
    // No fastio for interactive problems
    // fastio;


}

void solve(int tc)
{
    int l, r, x, y, status = 1;
    char ch;

    cin >> l >> r;
    x = 0, y = l;

    while(status != -1)
    {
        x = -x, y = 2 * l - y;
        cout << "P " << x << ' ' << y << endl;
        fflush(stdout);

        cin >> ch >> status;
        if(status == -1) exit(1);

        cin >> ch >> x >> y;
        cin >> ch >> status;
    }
}

signed main()
{
    pre();

    int tc, tt = 1;
    cin >> tt;

    for(tc = 1; tc <= tt; tc++)
    {
        solve(tc);
        cout << endl;
    }

    return 0;
}
```

</details>
</details>
</details>
