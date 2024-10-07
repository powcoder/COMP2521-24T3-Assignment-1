# COMP2521 24T3 - Assignment 1

## 1. Assignment Overview
- **Course Information**: COMP2521 24T3, Data Structures and Algorithms course, School of Computer Science and Engineering, University of New South Wales
- **Assignment Contribution**: Contributes 15% to the final grade
- **Submission Requirements**
    - **Deadline**: 8 pm on Monday of Week 7
    - **Files to Submit**: Mset.c, MsetStructs.h, and analysis.txt
    - **Submission Method**: Command line ($ give cs2521 ass1 Mset.c MsetStructs.h analysis.txt) or give's web interface
    - **Notes**: Multiple submissions are allowed, and only the last one will be marked. Check after submission.
- **Grading Criteria**
    - **Correctness (75%)**
        - Includes the correctness of basic operations (such as insertion, deletion, getting size, getting total count, getting element count, printing, etc.) and advanced operations (such as union, intersection, inclusion check, equality check, getting most common elements, etc.), as well as the correctness of related operations after updating the balanced binary search tree and cursor operations.
        - Each operation has a corresponding score percentage, and there will be deductions for memory errors/leaks.
    - **Complexity Analysis (15%)**: The correctness of the complexity analysis in analysis.txt and the quality of explanations.
    - **Code Style (10%)**: Evaluation includes indentation, space usage, function usage, code decomposition, and comments.

## 2. Assignment Content

### 2.1 Multiset Abstract Data Type (ADT)
- **Definition**
    - A collection that allows duplicate elements, where each element has a count indicating the number of times it appears in the collection.
    - It is an abstract data type, and the focus is on the set of operations. The implementation details are not important as long as the desired behavior is presented to the user.
- **Operation Requirements**
    - **Basic Operations (Part 1)**
        - **MsetNew**: Creates a new empty Multiset with a time complexity requirement of $O(1)$.
        - **MsetFree**: Frees all memory allocated to the Multiset with a time complexity of $O(n)$.
        - **MsetInsert**: Inserts one element into the Multiset. If the element is equal to UNDEFINED, nothing is done. The time complexity is $O(h)$.
        - **MsetInsertMany**: Inserts a given number of elements. If the element is equal to UNDEFINED or the number is 0 or less, nothing is done. The time complexity is $O(h)$.
        - **MsetDelete**: Deletes one element from the Multiset with a time complexity of $O(h)$.
        - **MsetDeleteMany**: Deletes a given number of elements with a time complexity of $O(h)$.
        - **MsetSize**: Returns the number of distinct elements in the Multiset with a time complexity of $O(1)$.
        - **MsetTotalCount**: Returns the sum of the counts of all elements in the Multiset with a time complexity of $O(1)$.
        - **MsetGetCount**: Returns the count of an element in the Multiset. If the element is not in the Multiset, it returns 0. The time complexity is $O(h)$.
        - **MsetPrint**: Prints the Multiset to a file. The elements are sorted in ascending order and in the format of `{(element, count),...}`. The time complexity is $O(n)$.
    - **Advanced Operations (Part 2)**
        - **MsetUnion**: Given two Multisets, returns their union. The count of each element in the new Multiset is the maximum of its counts in the two original Multisets. The time complexity needs to be analyzed and written in analysis.txt. Methods like converting the tree to an array or list and then processing are not allowed.
        - **MsetIntersection**: Given two Multisets, returns their intersection. The count of each element in the new Multiset is the minimum of its counts in the two original Multisets. The time complexity needs to be analyzed and written in analysis.txt, and certain processing methods are prohibited.
        - **MsetIncluded**: Given two Multisets, determines if one is included in the other based on element counts. The time complexity needs to be analyzed and written in analysis.txt, and certain processing methods are prohibited.
        - **MsetEquals**: Given two Multisets, determines if they are equal based on whether the elements and counts are exactly the same. The time complexity needs to be analyzed and written in analysis.txt, and certain processing methods are prohibited.
        - **MsetMostCommon**: Given a Multiset, an integer, and an array, stores the most common elements in the Multiset in descending order of count into the array and returns the number of elements stored. The time complexity needs to be analyzed and written in analysis.txt.
    - **Balanced Binary Search Tree (Part 3)**
        - Update the implementation to use a height-balanced binary search tree so that MsetInsert, MsetInsertMany, MsetDelete, and MsetDeleteMany have a worst-case time complexity of $O(log n)$, and ensure that the underlying binary search tree of any Multiset is always height-balanced.
    - **Cursor Operations (Part 4)**
        - **MsetCursorNew**: Creates a new cursor for a given Multiset, initially positioned at the start of the Multiset.
        - **MsetCursorFree**: Frees all memory allocated to a given cursor.
        - **MsetCursorGet**: Returns the element at the cursor's position and its count. If the cursor is at the start or end of the Multiset, it returns {UNDEFINED, 0}.
        - **MsetCursorNext**: Moves the cursor to the next largest element. If there is no next largest element, it moves to the end of the Multiset. If the cursor is already at the end, it does not move. Returns false if the cursor is at the end after the operation, otherwise returns true.
        - **MsetCursorPrev**: Moves the cursor to the next smallest element. If there is no next smallest element, it moves to the start of the Multiset. If the cursor is already at the start, it does not move. Returns false if the cursor is at the start after the operation, otherwise returns true.
        - All cursor operations should have a worst-case time complexity of $O(1)$ or $O(log n)$. The design and implementation and how the time complexity requirement is met need to be explained in analysis.txt.

### 2.2 Assignment File Description
- **Initial Files**
    - **Makefile**: A set of dependencies used to control compilation.
    - **Mset.h**: The interface to the Multiset ADT, which cannot be modified.
    - **Mset.c**: The implementation of the Multiset ADT (initially incomplete).
    - **MsetStructs.h**: The definition of structs used in the Multiset ADT (initially incomplete).
    - **testMset.c**: A main program containing some basic tests for the Multiset ADT.
    - **analysis.txt**: A template for entering the time complexity analysis of selected functions.
- **Struct Usage Requirements**
    - Must use `struct node` for binary search tree nodes.
    - The elements of the multiset must be stored in the `elem` fields of `struct node`, and their counts must be stored in the `count` fields.
    - The `left` and `right` pointers are used to connect a tree node to its left and right subtrees and cannot be used for other purposes.
    - The `tree` field must point to the binary search tree that stores all the elements of the multiset.

### 2.3 Testing and Debugging
- **Testing**
    - The `testMset.c` is provided as a basic test program. It can be compiled by `make` and run by `./testMset`.
    - The tests are assertion-based, and a failed test will cause the program to exit. A test can be ignored by commenting out the corresponding test function.
    - It is recommended to add your own test functions.
- **Debugging**
    - Students are expected to know basic debugging methods, such as using print statements, basic GDB commands, and running Valgrind.
    - The use of GDB and Valgrind can be learned in relevant lab exercises.

## 3. Background Knowledge
- **Prerequisite Knowledge Requirements**: Recursion, analysis of algorithms, abstract data types, binary search trees, balanced binary search trees (including AVL trees)
- **Multiset Related Concepts**
    - Similar to the concept of a set but allows duplicate elements, and each element has a count.
    - It can be represented in the form of elements and their counts enclosed in curly braces, such as `{(1, 3), (4, 2)}`, indicating that element 1 appears 3 times and element 4 appears 2 times.
    - Related symbolic notations are defined, such as `cA(x)` representing the count of element `x` in multiset `A`, and if `x` is not in `A`, then `cA(x)=0`. The empty multiset is denoted by `∅`.

# COMP2521 24T3 Assignment 1
# 加微信 powcoder

# QQ 1823890830

# Programming Help Add Wechat powcoder

# Email: powcoder@163.com

