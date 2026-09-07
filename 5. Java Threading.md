# Java Multithreading & Parallel Programming Guide

A comprehensive guide to multithreading concepts in Java, explaining operating system thread fundamentals, practical concurrent programming examples, code explanations, and expected outputs.

---

## Table of Contents
1. [Introduction to Threading](#1-introduction-to-threading)
   - [What is a Thread?](#what-is-a-thread)
   - [Why is Multithreading Needed?](#why-is-multithreading-needed)
   - [Why is Multithreading Required in Operating Systems?](#why-is-multithreading-required-in-operating-systems)
2. [Problem 1: Parallel Sum of an Array](#2-problem-1-parallel-sum-of-an-array)
   - [Code Implementation](#code-implementation-array-sum)
   - [Code Explanation](#code-explanation-array-sum)
   - [Expected Output](#expected-output-array-sum)
3. [Problem 2: Parallel Matrix Row Multiplication](#3-problem-2-parallel-matrix-row-multiplication)
   - [Code Implementation](#code-implementation-matrix-scale)
   - [Code Explanation](#code-explanation-matrix-scale)
   - [Expected Output](#expected-output-matrix-scale)

---

## 1. Introduction to Threading

### What is a Thread?
A **thread** is the smallest execution unit within a computer program that can be scheduled and managed independently by the operating system CPU scheduler. Multiple threads can exist within a single process, sharing common resources such as memory space, open files, and code segments, while maintaining their own private execution context (registers, program counter, and execution stack).

### Why is Multithreading Needed?
1. **Parallel Execution & Multi-core Utilization:** Modern computer hardware features CPUs with multiple physical cores. Single-threaded applications can only execute on one core at a time, leaving remaining processing power underutilized. Multithreading allows programs to distribute workloads across multiple cores simultaneously.
2. **Improved Responsiveness:** In interactive applications (such as desktop GUIs or web applications), running time-consuming or background operations (e.g., file downloads, database queries) on separate worker threads prevents the main UI thread from freezing.
3. **High Throughput:** Applications processing large datasets or handling simultaneous web client requests (like web servers) achieve significantly higher processing throughput by executing independent tasks concurrently.

### Why is Multithreading Required in Operating Systems?
Operating Systems depend on multithreading for efficient system kernel management and process execution:
* **Efficient Resource Management:** Creating a process requires allocating a distinct virtual memory space, file descriptor tables, and security contexts, which is computationally expensive. Threads share process memory, making thread creation and context switching far cheaper than process-level context switching.
* **Asynchronous I/O Handling:** When a thread performs an input/output operation (e.g., waiting for disk reading or network packets), the operating system can put that specific thread in a waiting state while switching execution to another ready thread, ensuring the CPU remains busy and efficient.
* **Concurrent System Services:** Operating systems use kernel threads to handle concurrent background tasks—such as memory management (garbage collection/paging), hardware interrupt servicing, and file system synchronization—without interrupting user applications.

---

## 2. Problem 1: Parallel Sum of an Array

### Problem Statement
Divide an array of numbers into two equal halves. Create two threads where **Thread 1** calculates the sum of the first half and **Thread 2** calculates the sum of the second half. The main thread then adds both partial sums together to display the total sum.

### Code Implementation (Array Sum)
```java
class SumTask implements Runnable {
    private final int[] arr;
    private final int start;
    private final int end;
    private int partialSum;

    public SumTask(int[] arr, int start, int end) {
        this.arr = arr;
        this.start = start;
        this.end = end;
    }

    public int getPartialSum() {
        return partialSum;
    }

    @Override
    public void run() {
        partialSum = 0;
        for (int i = start; i < end; i++) {
            partialSum += arr[i];
        }
    }
}

public class ArraySum {
    public static void main(String[] args) throws InterruptedException {
        int[] numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}; // Total sum = 55
        int mid = numbers.length / 2;

        SumTask task1 = new SumTask(numbers, 0, mid);
        SumTask task2 = new SumTask(numbers, mid, numbers.length);

        Thread t1 = new Thread(task1);
        Thread t2 = new Thread(task2);

        // Start worker threads
        t1.start();
        t2.start();

        // Wait for worker threads to complete execution
        t1.join();
        t2.join();

        int totalSum = task1.getPartialSum() + task2.getPartialSum();

        System.out.println("Thread 1 Sum: " + task1.getPartialSum());
        System.out.println("Thread 2 Sum: " + task2.getPartialSum());
        System.out.println("Total Array Sum: " + totalSum);
    }
}
```

### Code Explanation (Array Sum)
1. **`SumTask` Implementation (`Runnable` Interface):**
   - The `SumTask` class implements Java's `Runnable` interface, allowing instances to be executed by a thread.
   - It stores references to the shared array (`arr`), processing index limits (`start` and `end`), and a variable to hold the calculated sum (`partialSum`).
   - The `run()` method loops from `start` (inclusive) to `end` (exclusive) and accumulates the values into `partialSum`.

2. **Array Division & Thread Creation (`main` method):**
   - The main thread creates an integer array of 10 elements and determines the midpoint (`mid = 5`).
   - Two task instances are created: `task1` processes indices `0` to `4` (`{1, 2, 3, 4, 5}`), and `task2` processes indices `5` to `9` (`{6, 7, 8, 9, 10}`).
   - Two `Thread` objects (`t1` and `t2`) are initialized with their respective tasks.

3. **Thread Execution and Synchronization:**
   - `t1.start()` and `t2.start()` invoke the Operating System scheduler to run both threads concurrently.
   - `t1.join()` and `t2.join()` block the execution of the main thread until `t1` and `t2` have finished processing. This prevents the main thread from reading partial sums before calculation completes.
   - Once both threads finish, the main thread reads the partial sums via `getPartialSum()`, adds them together, and prints the results.

### Expected Output
```text
Thread 1 Sum: 15
Thread 2 Sum: 40
Total Array Sum: 55
```

---

## 3. Problem 2: Parallel Matrix Row Multiplication

### Problem Statement
Given a $3 	imes 3$ matrix and a single scalar value, create 3 separate worker threads where each thread multiplies a single row of the matrix by the scalar value simultaneously.

### Code Implementation (Matrix Scale)
```java
public class MatrixScale {
    private static final int ROWS = 3;
    private static final int COLS = 3;
    private static final int[][] matrix = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    static class RowTask implements Runnable {
        private final int rowIndex;
        private final int scalar;

        public RowTask(int rowIndex, int scalar) {
            this.rowIndex = rowIndex;
            this.scalar = scalar;
        }

        @Override
        public void run() {
            for (int j = 0; j < COLS; j++) {
                matrix[rowIndex][j] *= scalar;
            }
        }
    }

    public static void main(String[] args) throws InterruptedException {
        Thread[] threads = new Thread[ROWS];
        int scalar = 5;

        // Create and start a thread for each row
        for (int i = 0; i < ROWS; i++) {
            threads[i] = new Thread(new RowTask(i, scalar));
            threads[i].start();
        }

        // Wait for all threads to complete
        for (int i = 0; i < ROWS; i++) {
            threads[i].join();
        }

        // Display the modified matrix result
        System.out.println("Matrix after scalar multiplication (" + scalar + "x):");
        for (int i = 0; i < ROWS; i++) {
            for (int j = 0; j < COLS; j++) {
                System.out.print(matrix[i][j] + "	");
            }
            System.out.println();
        }
    }
}
```

### Code Explanation (Matrix Scale)
1. **Shared Memory Structure:**
   - The matrix `matrix` is defined as a `private static final` 2D array accessible to all inner static classes within `MatrixScale`.
   - Because each thread accesses and modifies a completely distinct row index (`matrix[rowIndex]`), no data races or thread contention occur during parallel write operations.

2. **Row Multiplier Task (`RowTask`):**
   - Each `RowTask` instance is instantiated with a specific `rowIndex` and target `scalar` value.
   - Inside `run()`, a single `for` loop iterates across all columns `j` of that assigned row and multiplies each element by `scalar` in-place.

3. **Parallel Dispatch and Synchronization Loop:**
   - An array of `Thread` objects (`threads`) of length equal to `ROWS` (3) is instantiated.
   - A `for` loop instantiates and starts each worker thread (`threads[i].start()`), assigning Thread 0 to Row 0, Thread 1 to Row 1, and Thread 2 to Row 2.
   - A second `for` loop calls `join()` on each thread element to ensure all 3 rows have finished scalar multiplication before the main thread attempts to display the matrix.
   - Finally, the main thread iterates over the matrix and prints the scaled values in tabular format.

### Expected Output
```text
Matrix after scalar multiplication (5x):
5	10	15	
20	25	30	
35	40	45	
```
