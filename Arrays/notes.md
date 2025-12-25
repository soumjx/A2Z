# 📘 STRIVER A2Z ARRAYS — MASTER NOTES (STEP 3.1–3.4)

> These are not casual notes.
> This is a **personal DSA grimoire** — something you can revisit years later and still hear Striver’s logic guiding your answers.

---

# 🔹 WHAT IS AN ARRAY (Foundational Theory)

## Definition

An **array** is a data structure that stores **elements of the same data type** in **contiguous memory locations**.

| Allowed    | Not Allowed  |
| ---------- | ------------ |
| All int    | int + string |
| All char   | char + float |
| All string | mixed        |

An array can store:

* Integers
* Characters
* Strings
* Pairs

But **only one data type per array**.

---

## 🔹 Declaration

### C++

```cpp
int arr[6];
```

### Java

```java
int[] arr = new int[6];
```

---

## 🔹 Default Values

| Where declared | Initial value   |
| -------------- | --------------- |
| Inside main    | Garbage values  |
| Global         | Filled with `0` |

---

## 🔹 Maximum Size

| Location    | Maximum Size |
| ----------- | ------------ |
| Inside main | 10⁶          |
| Global      | 10⁷          |

---

## 🔹 Indexing

| Description | Value |
| ----------- | ----- |
| First index | 0     |
| Last index  | n-1   |

Access using:

```cpp
arr[i]
```

---

## 🔹 Memory Layout

| Element | Address |
| ------- | ------- |
| arr[0]  | X       |
| arr[1]  | X+1     |
| arr[2]  | X+2     |
| ...     | ...     |

* `X` is a random base address
* Memory is contiguous
* Direct address access is impossible
* Access is only via index

---

## 🔹 INTERVIEW STRATEGY RULE

Always follow:

**Brute → Better → Optimal**

You drive the interview by evolving your solution.

---

# 1️⃣ LARGEST ELEMENT IN ARRAY

### Brute Force

Sort the array and return the last element.

| TC         | SC   |
| ---------- | ---- |
| O(n log n) | O(1) |

---

### Optimal

```cpp
largest = arr[0];
for (int i = 0; i < n; i++) {
    if (arr[i] > largest) {
        largest = arr[i];
    }
}
```

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

---

# 2️⃣ SECOND LARGEST ELEMENT

### Brute Force

1. Sort the array
2. From `n-2`, find the first element ≠ largest

| TC                | SC   |
| ----------------- | ---- |
| O(n log n) + O(n) | O(1) |

---

### Better (Two Pass)

* Pass 1: Find largest
* Pass 2: Find max element `< largest`

| TC    | SC   |
| ----- | ---- |
| O(2n) | O(1) |

---

### Optimal (Single Pass)

**Logic**

* Track `largest`
* Track `secondLargest`
* If a value beats `largest`, old `largest` becomes `secondLargest`

```cpp
largest = arr[0];
second = INT_MIN;

for (int i = 1; i < n; i++) {
    if (arr[i] > largest) {
        second = largest;
        largest = arr[i];
    }
    else if (arr[i] < largest && arr[i] > second) {
        second = arr[i];
    }
}
```

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

---

# 3️⃣ CHECK IF ARRAY IS SORTED

**Condition**

`arr[i] >= arr[i-1]`

```cpp
for (int i = 1; i < n; i++) {
    if (arr[i] < arr[i-1]) return false;
}
return true;
```

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

---

# 4️⃣ REMOVE DUPLICATES FROM SORTED ARRAY (IN-PLACE)

### Brute Force

Use a Set.

| TC         | SC   |
| ---------- | ---- |
| O(n log n) | O(n) |

---

### Optimal — Two Pointer

**Concept**
Unique elements are compacted at the front.

```cpp
int i = 0;
for (int j = 1; j < n; j++) {
    if (arr[j] != arr[i]) {
        arr[i + 1] = arr[j];
        i++;
    }
}
return i + 1;
```

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

---

# 🧠 CORE INTERVIEW MEMORY LOCK

| Problem           | Optimal TC |
| ----------------- | ---------- |
| Largest           | O(n)       |
| Second Largest    | O(n)       |
| Check Sorted      | O(n)       |
| Remove Duplicates | O(n)       |

---


**Next Striver lecture?**
Drop it and we’ll carve the next chapter into your grimoire 📚✨
