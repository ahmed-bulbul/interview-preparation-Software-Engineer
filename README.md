# فَسَقٰی لَهُمَا ثُمَّ تَوَلّٰۤی اِلَی الظِّلِّ فَقَالَ رَبِّ اِنِّیۡ لِمَاۤ اَنۡزَلۡتَ اِلَیَّ مِنۡ خَیۡرٍ فَقِیۡرٌ ﴿۲۴﴾
তখন মূসা তাদের পক্ষে (পশুগুলোকে) পানি পান করিয়ে দিল। তারপর ছায়ায় ফিরে গেল এবং বলল, ‘হে আমার রব, নিশ্চয় আপনি আমার প্রতি যে অনুগ্রহই নাযিল করবেন, আমি তার মুখাপেক্ষী’।
# Interview Preparation: Software Engineer - Java


## Table of Contents
- [Basic Problems and Data Structures](#basic-problems-and-data-structures)
- [Core Java Questions](#core-java-questions)
- [OOP Concepts](#oop-concepts)
- [Java 8 Features](#java-8-features)
- [Threading](#threading)
- [Collections Framework](#collections-framework)
- [Design Patterns](#design-patterns)
- [System Design Questions](#system-design-questions)
- [SQL Questions](#sql-questions)
- [Hibernate Questions](#hibernate-questions)
- [Spring & Spring Boot Questions](#spring-and-spring-boot-questions)
- [Spring Security Questions](#spring-security-questions)
- [Docker Questions](#docker-questions)
- [Kubernetes Questions](#kubernetes-questions)
- [Real Interview Questions](#real-interview-questions)

---

## Basic Problems and Data Structures
1. **Find the second largest number in an array**

   **Solution:**
   ```java
   public class SecondLargest {
       public static int findSecondLargest(int[] nums) {
           if (nums == null || nums.length < 2) {
               throw new IllegalArgumentException("Array must contain at least two elements.");
           }

           int largest = Integer.MIN_VALUE;
           int secondLargest = Integer.MIN_VALUE;

           for (int num : nums) {
               if (num > largest) {
                   secondLargest = largest;
                   largest = num;
               } else if (num > secondLargest && num < largest) {
                   secondLargest = num;
               }
           }

           return secondLargest;
       }

       public static void main(String[] args) {
           int[] nums = {10, 20, 4, 45, 99, 99};
           System.out.println("Second largest: " + findSecondLargest(nums));
       }
   }
   ```

2. **Rotate an array**

   **Solution:**
   ```java
   import java.util.Arrays;

   public class RotateArray {
       public static void rotate(int[] nums, int k) {
           k = k % nums.length;
           reverse(nums, 0, nums.length - 1);
           reverse(nums, 0, k - 1);
           reverse(nums, k, nums.length - 1);
       }

       private static void reverse(int[] nums, int start, int end) {
           while (start < end) {
               int temp = nums[start];
               nums[start] = nums[end];
               nums[end] = temp;
               start++;
               end--;
           }
       }

       public static void main(String[] args) {
           int[] nums = {1, 2, 3, 4, 5, 6, 7};
           int k = 3;
           rotate(nums, k);
           System.out.println("Rotated array: " + Arrays.toString(nums));
       }
   }
   ```
 3. **Fibbonacci Series**

   **Solution:**
   ```java
   public class Fibbonacci {
       public static void main(String[] args) {
           int n = 10;
           int[] fib = new int[n];
           fib[0] = 0;
           fib[1] = 1;
           for (int i = 2; i < n; i++) {
               fib[i] = fib[i - 1] + fib[i - 2];
           }
           for (int i = 0; i < n; i++) {
               System.out.print(fib[i] + " ");
           }
   
           // Output: 0 1 1 2 3 5 8 13 21 34    
            //another approach
            int n = 10;
            int a = 0, b = 1;
            System.out.print(a + " " + b + " ");    
            for (int i = 2; i < n; i++) {
                int c = a + b;
                a = b;
                b = c;
                System.out.print(c + " ");
            }
       }
   
        
   }
   ```
4. **Factorial Number**

    **Solution:**
    ```java
    public class Factorial {
        public static void main(String[] args) {
            int n = 5;
            int fact = 1;
            for (int i = 1; i <= n; i++) {
                fact *= i;
            }
            System.out.println("Factorial of " + n + " is: " + fact);
        }
   
        //using recursion
        public static int factorial(int n) {
            if (n == 0) {
                return 1;
            } else {
                return n * factorial(n - 1);
            }
        }
   
   
    }
## Core Java Questions
1. **Java Memory Management and Garbage Collection**

   **Solution:**
   Java uses an automatic memory management system called Garbage Collection. It manages the lifecycle of objects in the heap memory, reclaiming memory occupied by objects that are no longer in use. This process prevents memory leaks and optimizes application performance. Key components include:

   - **Heap Memory:** Divided into Young Generation, Old Generation, and Permanent Generation (Metaspace in Java 8+).
   - **Stack memory :** Stores local variables and method parameters and function calls.
   - **Garbage Collector Algorithms:**
      - Serial GC
      - Parallel GC
      - G1 GC (Garbage-First)
      - ZGC (low-latency)

   Example:
   ```java
   public class GarbageCollectionDemo {
       public static void main(String[] args) {
           Runtime runtime = Runtime.getRuntime();
           System.out.println("Total Memory: " + runtime.totalMemory());
           System.out.println("Free Memory: " + runtime.freeMemory());

           for (int i = 0; i < 10000; i++) {
               String str = new String("Garbage Collection Example");
           }

           System.out.println("Free Memory before GC: " + runtime.freeMemory());
           System.gc();
           System.out.println("Free Memory after GC: " + runtime.freeMemory());
       }
   }
   ```




## Real Interview Questions
### Interview Overview
- ** Company : **Well Dev:** 
The interview consisted of two rounds:
- **HR Round:** 30 minutes
- **Technical Round:** 1 hour 30 minutes

### Questions Asked
1. Given an array `[2, 3, 5, 4]` and `k=2`, count pairs with a difference of 2
2. Runtime Polymorphism Problem
3. Stream API (Map, FlatMap)
4. Abstraction
5. Database Locking
6. Propagation Label
7. SOLID Principles
8. Spring Bean
9. IOC Container
10. Qualifier Annotation
11. Decode JWT token
12. Circular Dependency
13. Why Linked List is used over Array List
14. Polymorphism
15. Interface Segregation Principle
16. Bean Scope
17. Optional Class
18. Hibernate Entity State
