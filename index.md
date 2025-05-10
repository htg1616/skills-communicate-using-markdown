# 
It is so cool!
![Just an Image](https://github.com/user-attachments/assets/c24fcc81-c0b1-4b6b-a4fd-60dbb73d0b62)

``` c++
#include <bits/stdc++.h>
#define endl '\n'
#define X first
#define Y second
using namespace std;
typedef long long ll;
typedef pair<int, int> pii;
typedef pair<ll, ll> pll;

struct Trie {
    int unused = 1;
    vector<vector<int>> nxt;
    vector<bool> chk;

    Trie(int mx, int index) {
        nxt.assign(mx + 5, vector<int>(index));
        chk.assign(mx + 5, false);
    }

    void insert(string s) {
        int curr = 1;
        for (char c : s) {
            if (!nxt[curr][c - 'a'])
                nxt[curr][c - 'a'] = ++unused;
            curr = nxt[curr][c - 'a'];
        }
        chk[curr] = true;
    }

    bool find(string s) {
        int curr = 1;
        for (char c : s) {
            if (!nxt[curr][c - 'a'])
                return false;
            curr = nxt[curr][c - 'a'];
        }
        return true;
    }
};

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);

    int n, m;
    cin >> n >> m;
    Trie trie(500 * n, 26);

    for (int i = 0; i < n; i++) {
        string s;
        cin >> s;
        trie.insert(s);
    }

    int cnt = 0;
    for (int i = 0; i < m; i++) {
        string s;
        cin >> s;
        cnt += trie.find(s);
    }

    cout << cnt << endl;

    return 0;
}
```

- [ ] Complete Github Markdown Course
- [ ] Complete Reading Friedberg 2.4
- [ ] Study Trie structure
