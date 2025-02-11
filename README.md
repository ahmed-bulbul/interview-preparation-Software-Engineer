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
    ```
5. **Reverse a String**

   **Solution:**
   ```java
   public class ReverseString {
       public static void main(String[] args) {
           String str = "Hello, World!";
           String reversed = "";
           for (int i = str.length() - 1; i >= 0; i--) {
               reversed += str.charAt(i);
           }
           System.out.println("Reversed string: " + reversed);
   }
   }
   ```
6. **Prime Number**

      **Solution:**
      ```java
      public class PrimeNumber {
          public static void main(String[] args) {
              int num = 17;
              boolean isPrime = true;
              for (int i = 2; i <= Math.sqrt(num); i++) {
                  if (num % i == 0) {
                      isPrime = false;
                      break;
                  }
              }
              if (isPrime) {
                  System.out.println(num + " is a prime number.");
              } else {
                  System.out.println(num + " is not a prime number.");
              }
          }
      }
      ```
7. **Reverse Linked List**

    **Solution:**
    ```java
    class Node {
        int data;
        Node next;
    
        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }
    
    public class ReverseLinkedList {
    
        static Node reverse(Node head) {
            Node curr = head, prev = null, next;
    
            while (curr != null) {
                next = curr.next;
                curr.next = prev;
                prev = curr;
                curr = next;
            }
    
            return prev;
        }
    
        static void printList(Node node) {
            while (node != null) {
                System.out.print(" " + node.data);
                node = node.next;
            }
        }
    
        public static void main(String[] args) {
    
            // Create a hard-coded linked list:
            // 1 -> 2 -> 3 -> 4 -> 5
            Node head = new Node(1);
            head.next = new Node(2);
            head.next.next = new Node(3);
            head.next.next.next = new Node(4);
            head.next.next.next.next = new Node(5);
    
            System.out.print("Given Linked List:");
            printList(head);
    
            head = reverse(head);
    
            System.out.print("\nReversed Linked List:");
            printList(head);
          }
     }
     ```
8. **Java program to find duplicate characters in a  string**

    **Solution:**
    ```java
    import java.util.*;

    public class DuplicateCharacters {
        public static void main(String[] args) {
            String str = "Java program to find duplicate characters in a string";
            Map<Character, Integer> charCountMap = new HashMap<>();
            for (char c : str.toCharArray()) {
                charCountMap.put(c, charCountMap.getOrDefault(c, 0) + 1);
            }
            for (Map.Entry<Character, Integer> entry : charCountMap.entrySet()) {
                if (entry.getValue() > 1) {
                    System.out.println(entry.getKey() + " occurs " + entry.getValue() + " times");
                }
            }
        }
    } 
    ```
9. **Java program to count the number of words in a string** 

    **Solution:**
    ```java
    import java.util.*;
    public class CountWords {
        public static void main(String[] args) {
            System.out.println("Enter the String"); 
            Scanner sc = new Scanner(System.in); 
            String s = sc.nextLine(); 
            int count = 1; 
            for (int i = 0; i < s.length() - 1; i++) { 
                if ((s.charAt(i) == ' ') && (s.charAt(i + 1) != ' ')) { 
                    count++; 
                } 
            } 
            System.out.println("Number of words in a string: " +count); 
        }
    }
    ```


**Must read** 

    𝗔𝗿𝗿𝗮𝘆𝘀
    1. Two Sum 
    - https://lnkd.in/dWDJFCrk
    2. Best Time to Buy and Sell Stock
    - https://lnkd.in/dbfXdHcc
    3. Maximum Subarray
    - https://lnkd.in/dA3e79e7
    4. Container with Most Water
    - https://lnkd.in/derBVWA2
    5. Rotate Array
    - https://lnkd.in/d3iAd_ye

    𝗦𝘁𝗿𝗶𝗻𝗴𝘀
    1. Reverse String
    - https://lnkd.in/dSYxrHkt
    2. Valid Palindrome
    - https://lnkd.in/dNTpQFit
    3. Longest Substring Without Repeating Characters
    - https://lnkd.in/dMYzuAY4
    4. Group Anagrams
    - https://lnkd.in/dZAMtWYM
    5. Longest Palindromic Substring
    - https://lnkd.in/dnk7bi7m

    𝗟𝗶𝗻𝗸𝗲𝗱 𝗟𝗶𝘀𝘁
    1. Reverse Linked List
    - https://lnkd.in/drbzn2b6
    2. Merge Two Sorted Lists
    - https://lnkd.in/d7dPE39P
    3. Remove Nth Node From End of List
    - https://lnkd.in/dhwSrxbu
    4. Linked List Cycle
    - https://lnkd.in/dvymdefx
    5. Intersection of Two Linked Lists
    - https://lnkd.in/dfJKZ2dZ

    𝗧𝗿𝗲𝗲𝘀
    1. Maximum Depth of Binary Tree
    - https://lnkd.in/dCMEXszH
    2. Validate Binary Search Tree
    - https://lnkd.in/dZVA-vNR
    3. Symmetric Tree
    - https://lnkd.in/ddx6A8Zw
    4. Binary Tree Level Order Traversal
    - https://lnkd.in/diR5nX4U
    5. Lowest Common Ancestor of a Binary Tree
    - https://lnkd.in/dFkJwkaV

    𝗚𝗿𝗮𝗽𝗵𝘀
    1. Number of Islands
    - https://lnkd.in/drj5P3bf
    2. Course Schedule
    - https://lnkd.in/duvfs54r
    3. Word Ladder
    - https://lnkd.in/dmTspiu3
    4. Clone Graph
    - https://lnkd.in/dXYJsBMY
    5. Network Delay Time
    - https://lnkd.in/d3WVx_JP

    𝗦𝗲𝗮𝗿𝗰𝗵𝗶𝗻𝗴 & 𝗦𝗼𝗿𝘁𝗶𝗻𝗴 
    1. Merge Sort
    - https://lnkd.in/d5TVqNCE
    2. Quick Sort
    - https://lnkd.in/d5TVqNCE
    3. Binary Search
    - https://lnkd.in/dQNu5M-V
    4. Search in Rotated Sorted Array
    - https://lnkd.in/dWMGpD5e
    5. First Bad Version
    - https://lnkd.in/dBpRdqwt

    𝗗𝘆𝗻𝗮𝗺𝗶𝗰 𝗣𝗿𝗼𝗴𝗿𝗮𝗺𝗺𝗶𝗻𝗴 
    1. Fibonacci Number
    - https://lnkd.in/dJqY369E
    2. Climbing Stairs
    - https://lnkd.in/dK8UxFsq
    3. Longest Increasing Subsequence
    - https://lnkd.in/dSkJXnDp
    4. Maximum Subarray Sum
    - https://lnkd.in/dA3e79e7
    5. Coin Change
    - https://lnkd.in/d-ByK5Fx



 
   
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

2. **What is the difference between JDK, JRE, and JVM?**
   - **Answer:**
       - **JDK (Java Development Kit):** Contains tools for developing Java applications, including the compiler and debugger.
       - **JRE (Java Runtime Environment):** Provides libraries and JVM for running Java applications.
       - **JVM (Java Virtual Machine):** Executes Java bytecode and provides platform independence.
       - 
3. **What is the difference between final, finally, and finalize?**
   - **Answer:**
       - **final:** A keyword for constants, methods that cannot be overridden, or classes that cannot be inherited.
       - **finally:** A block to execute cleanup code, always executed.
       - **finalize():** A method called by the Garbage Collector before object destruction.

4. **What is the difference between static and non-static methods?**
   - **Answer:**
       - **static:** Belong to the class itself and can be called without creating an instance.
       - **non-static:** Belong to instances of the class and require an instance to be created.
     
5.  **What is the difference between HashMap and ConcurrentHashMap?**
    - **Answer:**
        - **HashMap:** Not thread-safe; can have null keys/values.
        - **ConcurrentHashMap:** Thread-safe; doesn’t allow null keys or values.
6. **Why String is immutable?**

    - **উত্তর:**

      **`String` ইমিউটেবল কেন?**
      জাভাতে `String` ইমিউটেবল (পরিবর্তন অযোগ্য) হওয়ার কারণ হলো এটি সিকিউরিটি, পারফরম্যান্স এবং থ্রেড সেফটি নিশ্চিত করে। এটি ডিজাইনে এমনভাবে তৈরি করা হয়েছে যাতে এটি কার্যকর এবং নিরাপদ হয়।

      **কারণসমূহ:**
        1. **সিকিউরিটি:**  
           `String` অনেক জায়গায় ব্যবহৃত হয় যেমন ডাটাবেস ইউআরএল, ইউজারনেম, পাসওয়ার্ড। ইমিউটেবল হওয়ার কারণে, একবার তৈরি হওয়ার পর এটি পরিবর্তন করা যায় না, যা ডেটার নিরাপত্তা নিশ্চিত করে।

        2. **থ্রেড সেফটি:**  
           ইমিউটেবল `String` একাধিক থ্রেড দ্বারা শেয়ার করা হলে কোনো থ্রেড এটি পরিবর্তন করতে পারে না। এটি ডেটার সঠিকতা এবং নিরাপত্তা বজায় রাখে।

        3. **স্ট্রিং পুলিং:**  
           ইমিউটেবল হওয়ার কারণে, `String` অবজেক্টগুলো **স্ট্রিং পুল**-এ সংরক্ষণ করা হয় এবং একাধিক রেফারেন্স একই অবজেক্ট শেয়ার করতে পারে। এটি মেমোরি সাশ্রয় করে।

        4. **পারফরম্যান্স:**  
           `String` ইমিউটেবল হওয়ায় এর `hashCode()` একবার গণনা করার পর সংরক্ষণ করা যায়। এটি ডেটা স্ট্রাকচার যেমন `HashMap` বা `HashSet`-এ ব্যবহারের সময় দ্রুত অ্যাক্সেস নিশ্চিত করে।

        5. **ডিজাইন সিম্পলিসিটি:**  
           ইমিউটেবল `String` ব্যবহারের ফলে জাভার ডিজাইন এবং কোড লেখা সহজ হয়। একবার তৈরি হলে এটি পরিবর্তনযোগ্য না হওয়ায় বাগ সৃষ্টির সম্ভাবনা কমে।

      **কীভাবে ইমিউটেবল?**
        - `String` এর ভ্যালু একটি `final` char array-এ সংরক্ষণ করা হয়, যা সরাসরি পরিবর্তন করা যায় না।
        - কোনো পরিবর্তন করার চেষ্টা করলে একটি নতুন `String` অবজেক্ট তৈরি হয়।

      **উদাহরণ:**
      ```java
      public class Main {
          public static void main(String[] args) {
              String s1 = "Hello";
              String s2 = s1; // s1 এবং s2 একই অবজেক্ট শেয়ার করছে।
 
              s1 = s1.concat(" World"); // নতুন একটি স্ট্রিং অবজেক্ট তৈরি হয়।
              
              System.out.println("s1: " + s1); // আউটপুট: Hello World
              System.out.println("s2: " + s2); // আউটপুট: Hello
          }
      }
      ```

      **কী ঘটছে?**
        - `"Hello"` স্ট্রিং পুলে থাকে এবং `s1`, `s2` সেটি রেফারেন্স করে।
        - `s1.concat(" World")` একটি নতুন `String` অবজেক্ট তৈরি করে, কিন্তু পুরোনো `"Hello"` অপরিবর্তিত থাকে।

      **উপসংহার:**
        - `String` ইমিউটেবল হওয়ায়:
            - ডেটা সুরক্ষিত থাকে।
            - মেমোরি সাশ্রয় হয়।
            - থ্রেড সেফটি নিশ্চিত হয়।






## Threading
1. **How Synchronized works?**
    - **Answer:**
        - **Synchronized:** A keyword for constants, methods that cannot be overridden, or classes that cannot be inherited.
      - **synchronized:** A block to execute cleanup code, always executed.
      - **synchronized():** A method called by the Garbage Collector before object destruction.
      - Lock Acquisition:

      -When a thread reaches a synchronized block or method, it attempts to acquire the monitor lock of the object or class.
      -Blocking Other Threads:

      -If the lock is already held by another thread, the current thread is blocked until the lock is released. 
    ```java
    synchronized (this) {
        // Code to be synchronized
    }
    ```
2. **Explain Future and CompletableFuture.**
    - **Answer:**
        - **Future:** Represents async computation.
        - **CompletableFuture:** Enhances Future with callback methods.

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
