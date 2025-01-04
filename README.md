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
