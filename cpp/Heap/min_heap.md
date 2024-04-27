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

        while (2 * i + 1 < n) {
            int j = 2 * i + 1;
            if (j + 1 < n && h[j + 1] < h[j])
                j++;
            if (h[j] < h[i]) {
                swap(h[j], h[i]);
                i = j;
            } else break;
        }

        return min;
    }
};
```
