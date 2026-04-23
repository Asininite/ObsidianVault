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


# 🎯 Weighted Job Scheduling — Line-by-Line Explanation (C++)

Below is the same logic broken down so you can **reconstruct it during an interview**, not just memorize it.

---

## 🔧 Code (reference)

```cpp
struct Job {
    int start, end, profit;
};

bool compare(Job a, Job b) {
    return a.end < b.end;
}

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
    
    sort(jobs.begin(), jobs.end(), compare);
    
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

---

# 🧠 Step-by-step Explanation

---

## 1. Job Structure

```cpp
struct Job {
    int start, end, profit;
};
```

👉 Combines 3 arrays into one object  
So each job is easier to handle and sort.

---

## 2. Sorting Comparator

```cpp
bool compare(Job a, Job b) {
    return a.end < b.end;
}
```

👉 Sort jobs by **end time**

**Why?**

- Ensures when we process job `i`, all earlier jobs are already processed
    
- Makes binary search possible
    

---

## 3. Binary Search Function

```cpp
int findLastNonConflict(vector<Job>& jobs, int i)
```

👉 Goal: find **last job before `i` that doesn’t overlap**

---

### Inside it:

```cpp
int lo = 0, hi = i - 1;
```

Search only among previous jobs

---

```cpp
while (lo <= hi)
```

Standard binary search loop

---

```cpp
int mid = (lo + hi) / 2;
```

---

### Core condition:

```cpp
if (jobs[mid].end <= jobs[i].start)
```

👉 This means:

- Job `mid` ends before job `i` starts → valid
    

---

### Now check if it's the LAST valid one:

```cpp
if (mid + 1 <= hi && jobs[mid + 1].end <= jobs[i].start)
    lo = mid + 1;
else
    return mid;
```

👉 Move right if possible  
👉 Otherwise, this is the best match

---

```cpp
else {
    hi = mid - 1;
}
```

👉 If overlap → move left

---

```cpp
return -1;
```

👉 No valid job found

---

# 🚀 Main Function

---

## 4. Create Job List

```cpp
vector<Job> jobs(n);
for (int i = 0; i < n; i++) {
    jobs[i] = {startTime[i], endTime[i], profit[i]};
}
```

👉 Convert 3 arrays → 1 list of jobs

---

## 5. Sort Jobs

```cpp
sort(jobs.begin(), jobs.end(), compare);
```

👉 Critical step  
Everything depends on this ordering

---

## 6. DP Array

```cpp
vector<int> dp(n);
dp[0] = jobs[0].profit;
```

👉 `dp[i]` = max profit till job `i`

First job → only option is to take it

---

## 7. Main Loop

```cpp
for (int i = 1; i < n; i++)
```

Process each job

---

### Step A: Include current job

```cpp
int include = jobs[i].profit;
```

Start with its own profit

---

### Step B: Add compatible job profit

```cpp
int idx = findLastNonConflict(jobs, i);
if (idx != -1)
    include += dp[idx];
```

👉 If a valid previous job exists:

- Add best profit till that job
    

---

### Step C: Compare with excluding

```cpp
dp[i] = max(dp[i - 1], include);
```

👉 Two choices:

- Skip → `dp[i-1]`
    
- Take → `include`
    

Pick best

---

## 8. Final Answer

```cpp
return dp[n - 1];
```

👉 Maximum profit using all jobs

---

# 🔁 Full Logic in One Sentence

> For every job, decide whether taking it (plus best compatible past job) is better than skipping it.

---

# ⚡ Intuition Summary

- Sorting → gives order
    
- Binary search → finds valid past job fast
    
- DP → stores best decisions
    

---

# 🚨 Common Interview Questions

Be ready to answer:

- Why sort by end time?
    
- Why binary search works here?
    
- What if we use recursion?
    
- Can we optimize space?
    

---

# ⏱ Final Recall (10 sec)

- Sort by end
    
- For each job:
    
    - include = profit + dp[last valid job]
        
    - exclude = dp[i-1]
        
- Take max
    

---

If needed, I can:

- Convert this to **recursive + memoization**
    
- Give **step-by-step dry run**
    
- Or give a **similar question Meesho may twist from this**