```cpp
template<class T>
struct min_heap {
    vector<T> h;

    bool empty() {
        return h.empty();
    }

    int size() {
        return h.size();
    }

    void push(T x) {
        int i = size();
        h.push_back(x);
        int p = (i - 1) / 2;
        while (i && h[p] > h[i]) {
            swap(h[p], h[i]);
            i = p;
            p = (i - 1) / 2;
        }
    }

    T top() {
        if (empty()) return -1;
        return h[0];
    }

    T pop() {
        T min = h[0];
        swap(h[0], h.back());
        h.pop_back();
        int n = size();
        int i = 0;

        while (i < n) {
            int l = 2 * i + 1, r = l + 1;
            if (l < n && r < n) {
                if (h[l] < h[r] && h[l] < h[i])
                    swap(h[i], h[l]), i = l;
                else if (h[r] <= h[l] && h[r] < h[i])
                    swap(h[r], h[i]), i = r;
                else break;
            } else if (l < n && h[l] < h[i]) {
                swap(h[l], h[i]);
                i = l;
            } else if (r < n && h[r] < h[i]) {
                swap(h[r], h[i]);
                i = r;
            } else break;
        }

        return min;
    }
};
```