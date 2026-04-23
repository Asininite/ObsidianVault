## 🧾 Problem Statement

You are given three integer arrays:

- `startTime[i]` → start time of the **i-th job**
- `endTime[i]` → end time of the **i-th job**
- `profit[i]` → profit earned from the **i-th job**

Each job runs from `startTime[i]` to `endTime[i]`.

---

## ⚠️ Constraint

You **cannot select two jobs that overlap**.

Two jobs **do NOT overlap** if:

endTime[j] <= startTime[i]

---

## 🎯 Objective

Select a subset of non-overlapping jobs such that:

👉 **Total profit is maximized**

---

## 📥 Input Format

- Three arrays of size `n`:
    - `startTime[]`
    - `endTime[]`
    - `profit[]`

---

## 📤 Output Format

- Return a single integer:  
    👉 **Maximum profit you can achieve**

---

## 🧪 Example

### Input:

startTime = [1, 2, 3, 4]  
endTime   = [3, 5, 10, 6]  
profit    = [50, 20, 100, 70]

---

### Explanation:

Possible selections:

- Job 1 → profit = 50
- Job 4 → profit = 70
- Total = **120**

OR

- Job 3 alone → profit = 100

👉 Best = **120**

---

### Output:

120

---

## 🔒 Constraints (typical)

- `1 ≤ n ≤ 10^5`
- `1 ≤ startTime[i] < endTime[i] ≤ 10^9`
- `1 ≤ profit[i] ≤ 10^4`

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Job {
    int start, end, profit;
};

bool compare(Job a, Job b) {
    return a.end < b.end;
}

// Find last non-conflicting job using binary search
int findLastNonConflict(vector<Job>& jobs, int i) {
    int lo = 0, hi = i - 1;
    
    while (lo <= hi) {
        int mid = (lo + hi) / 2;
        
        if (jobs[mid].end <= jobs[i].start) {
            if (mid + 1 <= hi && jobs[mid + 1].end <= jobs[i].start)
                lo = mid + 1;
            else
                return mid;
        } else {
            hi = mid - 1;
        }
    }
    
    return -1;
}

int jobScheduling(vector<int>& startTime, vector<int>& endTime, vector<int>& profit) {
    int n = startTime.size();
    
    vector<Job> jobs(n);
    for (int i = 0; i < n; i++) {
        jobs[i] = {startTime[i], endTime[i], profit[i]};
    }
    
    // Step 1: Sort by end time
    sort(jobs.begin(), jobs.end(), compare);
    
    // Step 2: DP array
    vector<int> dp(n);
    dp[0] = jobs[0].profit;
    
    for (int i = 1; i < n; i++) {
        int include = jobs[i].profit;
        
        int idx = findLastNonConflict(jobs, i);
        if (idx != -1)
            include += dp[idx];
        
        dp[i] = max(dp[i - 1], include);
    }
    
    return dp[n - 1];
}
```

