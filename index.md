---
title: Data Structures and Algorithms Interview Questions
description: Comprehensive DSA study notes covering arrays, linked lists, trees, graphs, and common coding interview questions with solutions and MCQs.
keywords:
  - data structures interview questions
  - algorithm interview preparation
  - DSA study notes
  - coding interview questions
  - arrays linked lists stacks queues
  - binary trees graphs heaps
  - time complexity analysis
  - Python DSA
---

# DSA

## Overview

- **Data structures** are the building blocks of any computer program.
- They help in organizing and manipulating data efficiently.
- Without data structures, a computer cannot properly understand how to follow a program’s instructions.
- Data structures also define relationships between data elements.
- Examples include:
  - Arrays
  - Linked Lists
  - Stacks
  - Queues
  - Others
- Data structures provide:
  - Clarity
  - Organization
  - Structure to program code
- They help programmers ensure each line of code performs its function correctly.

---

## Basic Data Structures (Freshers)

### Question: What are Data Structures?

- A data structure is a **mechanical or logical way** to organize data within a program.
- The way data is organized determines program performance.
- There are many data structure types, each with different uses.
- While designing code, special attention is required for data organization.
- If data is not stored efficiently or structured correctly, overall code performance reduces.

### Question: Why create Data Structures?

- Data structures ensure each line of code works correctly and efficiently.
- They help programmers identify and fix code problems.
- They help create a clear and organized codebase.

### Question: What are some applications of Data Structures?

- Decision making
- Genetics
- Image processing
- Blockchain
- Numerical and statistical analysis
- Compiler design
- Database design
- Many more domains

### Question: Explain the process behind storing a variable in memory.

- A variable is stored based on required memory size.
- Steps:
  1. Required memory amount is assigned.
  2. Data is stored based on the data structure used.
  3. Dynamic allocation can ensure high efficiency and real-time access to storage units as needed.

### Question: What is the difference between file structure and storage structure?

- **File Structure:**
  - Represents data in secondary/auxiliary memory.
  - Example devices: hard disks, pen drives.
  - Data remains intact until manually deleted.
- **Storage Structure:**
  - Data is stored in main memory (RAM).
  - Data is deleted once the function using it is completely executed.
- Core difference:
  - Storage structure uses computer system memory.
  - File structure uses auxiliary memory.

### Question: Describe the types of Data Structures.

- **Linear Data Structure:**
  - Elements are arranged sequentially/linearly.
  - Each element is connected to previous and next nearest elements.
  - Examples: arrays, linked lists.
- **Non-Linear Data Structure:**
  - Elements are not arranged linearly/sequentially.
  - Cannot traverse all elements in one pass like linear structures.
  - Examples: trees, graphs.

### Question: What is a stack data structure? What are its applications?

- A stack represents application state at a specific time.
- Items are added and removed from the top.
- It is a linear data structure.
- Order of operation:
  - **LIFO** (Last In First Out)
  - **FILO** (First In Last Out)
- Real-life analogy: stack of clothes; last added comes out first.
- Applications:
  - Temporary storage in recursion
  - Redo/Undo in editors
  - String reversal
  - Parenthesis matching
  - Postfix to infix expressions
  - Function call order

### Question: What are stack operations?

- **push:** Add item to top; overflow if full.
- **pop:** Remove top item; underflow if empty.
- **top:** Return top item.
- **isEmpty:** True if empty, else false.
- **size:** Return stack size.

### Question: What is a queue data structure? What are its applications?

- A queue is a linear data structure for systematic list storage.
- Items are added at rear and removed from front.
- It is used when items wait for long periods (example: checkout process).
- Real-life analogy: customer queue; first served first.
- Applications:
  - BFS in graphs
  - OS job/disk/CPU scheduling
  - Call center call management

### Question: What are queue operations?

- **enqueue:** Add to rear; overflow if full.
- **dequeue:** Remove from front; underflow if empty.
- **isEmpty:** True if queue empty, else false.
- **rear:** Return rear element without removal.
- **front:** Return front element without removal.
- **size:** Return queue size.

### Question: Differentiate between stack and queue.

| Stack | Queue |
| --- | --- |
| Linear structure; add/remove at top | Linear structure; add at rear, remove at front |
| LIFO | FIFO |
| Insert = push | Insert = eneque |
| Delete = pop | Delete = dequeue |
| One pointer: top() for add/delete | Two pointers: front() and rear() |
| Used in recursion problems | Used in sequential processing |

### Question: How to implement a queue using stacks?

- Queue `q` can be implemented using `stack1` and `stack2`.
- Two methods (both use auxiliary space complexity **O(n)**):

#### Method: Make enqueue costly

- Oldest element stays on top of `stack1`.
- Dequeue becomes **O(1)**.
- `stack2` helps place element on top of `stack1`.

**Pseudocode (Enqueue, O(n))**
```text
enqueue(q, data):  
While stack1 is not empty:
     Push everything from stack1 to stack2.
      Push data to stack1
      Push everything back to stack1.
```

**Pseudocode (Dequeue, O(1))**
```text
deQueue(q):
 If stack1 is empty then error  else
 Pop an item from stack1 and return it
```

#### Method: Make dequeue costly

- Enqueue pushes new element to top of `stack1`; enqueue is **O(1)**.
- If `stack2` is empty during dequeue, move all from `stack1` to `stack2`.
- Top of `stack2` gives first enqueued element.
- Move operation is **O(n)**.

**Pseudocode (Enqueue, O(1))**
```text
enqueue(q, data):    
Push data to stack1
```

**Pseudocode (Dequeue, O(n))**
```text
dequeue(q): 
If both stacks are empty then raise error.
If stack2 is empty:  
While stack1 is not empty:
 push everything from stack1 to stack2. 
  Pop the element from stack2 and return it.
```

### Question: How to implement a stack using queues?

- Stack `s` can be implemented using `q1` and `q2`.
- Two methods:

#### Method: Make push costly

- Keep newly entered element at front of `q1`.
- Pop becomes **O(1)** by dequeue from `q1`.
- `q2` is auxiliary queue.

**Pseudocode (Push, O(n))**
```text
push(s, data):
    Enqueue data to q2
    Dequeue elements one by one from q1 and enqueue to q2.
    Swap the names of q1 and q2
```

**Pseudocode (Pop, O(1))**
```text
pop(s):
dequeue from q1 and return it.
```

#### Method: Make pop costly

- Push enqueues to `q1`, so push is **O(1)**.
- For pop:
  - Move all except last from `q1` to `q2`.
  - Dequeue last from `q1` as result.
  - Swap `q1` and `q2`.

**Pseudocode (Push, O(1))**
```text
push(s,data):
Enqueue data to q1
```

**Pseudocode (Pop, O(n))**
```text
pop(s): 
	Step1: Dequeue every elements except the last element from q1 and enqueue to q2.
	Step2: Dequeue the last item of q1, the dequeued item is stored in result variable.
 	Step3: Swap the names of q1 and q2 (for getting updated data after dequeue) 
 	Step4: Return the result.
```

### Question: What is an array data structure? What are its applications?

- An array stores data efficiently and supports easy access.
- It stores data in sequence (like a list).
- It can hold more data than a list as described.
- Created by combining several arrays; each gets a unique identifier.
- Data is stored in creation order.
- Applications:
  - Databases
  - Computer systems storing large data
  - Frequently accessed data (large text/images)

### Question: Types of arrays

- **One-dimensional array:**
  - Elements in contiguous memory.
  - Access via single index.
  - Linear sequence.
- **Two-dimensional array:**
  - Tabular format (rows, columns).
  - `M x N` structure.
- **Three-dimensional array:**
  - Rows, columns, and depth.
  - Cube-like structure.
  - Three subscripts:
    - Depth/layer = first index
    - Row = second index
    - Column = third index

### Question: What is a linked list? What are applications?

- Linked list is a series of connected nodes/items.
- Each entry points to next node.
- Node order depends on creation order.
- Applications:
  - Implementing stack, queue, binary tree, graph
  - Dynamic OS memory management
  - Round robin scheduling
  - Browser forward/backward operations

### Question: Types of linked lists

- **Singly Linked List**
  - Items linked via key.
  - Key identifies item (often unique).
  - Each item in separate node.
  - Node can be object or collection.
  - Add item: append at end.
  - Remove item: node deleted and replaced by another.
  - Key can be integer/string/another linked list.
  - Uses:
    - Grocery lists
    - Patient records
    - Time-sensitive data (stock prices, flight schedules)
- **Doubly Linked List**
  - Each node points next and previous.
  - Supports two-way access.
  - Node access by address and by index.
  - Good for fast access to large data.
  - Disadvantages:
    - Harder to maintain than singly linked list
    - Harder insert/delete than singly linked list
- **Circular Linked List**
  - Unidirectional.
  - Last node points to first.
- **Doubly Circular Linked List**
  - Each node points next and previous.
  - Last points to first.
  - First’s previous points to last.
- **Header List**
  - Has header node at beginning.
  - Useful for repetitive operations like counting elements.

### Question: Difference between array and linked list

| Arrays | Linked Lists |
| --- | --- |
| Same-type elements collection | Node collection (data + address) |
| Stored in single memory block | Elements stored randomly/anywhere |
| Fixed size at runtime | Size allocated dynamically |
| Elements independent | Elements dependent |
| Faster/easier access | Access takes time |
| Memory utilization ineffective | Memory utilization effective |
| Insert/delete slower | Insert/delete faster |

### Question: What is asymptotic analysis of an algorithm?

- Defines runtime performance using mathematical bounds.
- Covers:
  - Best case: **Omega (Ω)**
  - Average case: **Theta (θ)**
  - Worst case: **Big Oh (O)**

### Question: What is HashMap in data structures?

- HashMap uses hash table implementation.
- Gives constant time **O(1)** access if key is known.

### Question: Requirement for key/value objects in HashMap

- Objects used as key/value should implement:
  - `equals()`
  - `hashcode()`
- `hashcode()` used during insertion.
- `equals()` used during retrieval.

### Question: How HashMap handles collisions in Java

- Java `java.util.HashMap` uses **chaining**.
- If same key bucket collision occurs, values are stored in linked list chain in bucket.
- Worst case:
  - All keys same hashcode
  - Hash table becomes linked list
  - Search becomes **O(n)** instead of **O(1)**
- Hashing algorithm selection matters.

### Question: Time complexity of `get()` and `put()` in HashMap

- **O(1)**, assuming uniform bucket distribution by hash function.

---

## Advanced Data Structures (Experienced)

### Question: What is a binary tree? What are applications?

- Binary tree organizes data for efficient retrieval and manipulation.
- Uses leaves and nodes representation.
- Leaves represent data; nodes represent relationships.
- Each node has two children.
- Each child has one parent.
- Parent is closer to root.
- Node deletion removes from child and parent relationship context.
- Applications:
  - Network routing tables
  - Decision trees
  - Expression evaluation
  - Database indices

### Question: What is a binary search tree (BST)? What are applications?

- BST stores items in sorted order.
- Node stores key and value.
- Key accesses item; value determines item presence.
- Key/value can be integer/float/string/combinations.
- BST rules:
  1. Left subtree values `<=` parent value.
  2. Right subtree values `>=` parent value.
  3. Left and right subtrees are also BSTs.
- Applications:
  - Indexing and multilevel indexing
  - Search algorithm implementation
  - Organizing sorted data streams

### Question: What are tree traversals?

- Tree traversal = visiting all nodes.
- Root is starting point (first node, connected through edges).
- Types:

#### Inorder Traversal

- Steps:
  1. Traverse left subtree
  2. Visit root
  3. Traverse right subtree

```java
// Print inorder traversal of given tree.
void printInorderTraversal(Node root) 
{ 
    if (root == null) 
        return;
    //first traverse to the left subtree
    printInorderTraversal(root.left);
    //then print the data of node
    System.out.print(root.data + " ");
    //then traverse to the right subtree
    printInorderTraversal(root.right); 
}
```

- Use:
  - In BST, gives ascending order.

#### Preorder Traversal

- Steps:
  1. Visit root
  2. Traverse left subtree
  3. Traverse right subtree

```java
// Print preorder traversal of given tree.
void printPreorderTraversal(Node root) 
{ 
    if (root == null) 
        return; 
    //first print the data of node
    System.out.print(root.data + " ");
    //then traverse to the left subtree
    printPreorderTraversal(root.left);                    
    //then traverse to the right subtree
    printPreorderTraversal(root.right); 
}
```

- Uses:
  - Copy tree
  - Prefix expression generation

#### Postorder Traversal

- Steps:
  1. Traverse left subtree
  2. Traverse right subtree
  3. Visit root

```java
// Print postorder traversal of given tree.
void printPostorderTraversal(Node root) 
{ 
 if (root == null) 
     return;
 //first traverse to the left subtree
 printPostorderTraversal(root.left);                    
 //then traverse to the right subtree
 printPostorderTraversal(root.right);
 //then print the data of node
 System.out.print(root.data + " ");
}
```

- Uses:
  - Delete tree
  - Postfix expression generation

- Example traversal outputs:
  - Inorder: `[4, 2, 5, 1, 3]`
  - Preorder: `[1, 2, 4, 5, 3]`
  - Postorder: `[4, 5, 2, 3, 1]`

### Question: What is deque and its types? Applications?

- Deque allows insertions at both ends.
- Unlike regular array-end push/pop models.
- Useful for:
  - Inventory tracking
  - Task scheduling
  - Large data handling
- Types:
  - **Input Restricted Deque:** insertion at one end, deletion at both ends.
  - **Output Restricted Deque:** deletion at one end, insertion at both ends.
- Applications:
  - Can act as stack and queue
  - Browser history
  - OS job scheduling

### Question: Key operations on deque

- `insertFront()`
- `insertLast()`
- `deleteFront()`
- `deleteLast()` (described as deleting from front in given text)
- `getFront()`
- `getRear()`
- `isEmpty()`
- `isFull()`

### Question: What is a priority queue? Applications?

- Abstract data type similar to queue.
- Each element has priority.
- Removal order depends on priority.
- Same priority elements follow queue order.
- Applications:
  - Dijkstra, Prim MST
  - Huffman coding
  - Kth largest/smallest element finding

### Question: Compare priority queue implementations

| Operations | peek | insert | delete |
| --- | --- | --- | --- |
| Linked List | O(1) | O(n) | O(1) |
| Binary Heap | O(1) | O(log n) | O(log n) |
| Binary Search Tree | O(1) | O(log n) | O(log n) |

### Question: What is graph data structure and representations? Applications?

- Graph is non-linear structure with nodes (vertices) and edges.
- Edges connect node pairs.
- Representations:

#### Adjacency Matrix

- 2D array of size `V x V`.
- Simple representation.
- Remove edge in **O(1)**.
- Query edge `u -> v` in **O(1)**.
- Cons:
  - Sparse graphs still use large space.
  - Add vertex takes **O(V^2)**.
  - Neighbor computation takes **O(V)**.

#### Adjacency List

- Each node stores list of directly connected nodes.
- End node points to null to indicate end.
- Space: **O(|V| + |E|)**.
- Worst-case edges: `C(V,2)` using **O(V^2)**.
- Easier vertex insertion.
- Fast neighbor computation.
- Con:
  - Edge existence query `u -> v` can be **O(V)** worst case.

### Question: Difference between BFS and DFS

| Breadth First Search (BFS) | Depth First Search (DFS) |
| --- | --- |
| Breadth First Search | Depth First Search |
| Finds shortest path using Queue | Finds shortest path using Stack |
| Traverses same level before next | Goes deep until no unvisited nearby nodes |
| Slower than DFS | Faster than BFS |
| Better when target near source | Better when target far from source |
| Needs more memory | Needs less memory |
| Revisited nodes removed from queue | Visited nodes pushed/removed from stack when no nodes left |
| No backtracking | Recursive with backtracking |
| FIFO based | LIFO based |

### Question: What is AVL tree, operations, rotations, applications?

- AVL = height-balanced BST (Adelson, Velski, Landis).
- Balance condition:
  - Difference of left and right subtree heights is < 1.
- Balance factor:
  - `BalanceFactor = height(left-subtree) − height(right-subtree)`
- Operations:
  - **Insertion:** same as BST; rebalance if violated.
  - **Deletion:** same as BST; may require rebalancing rotations.
- Rotations:
  - **Left rotation:** inserted in right subtree of right subtree.
  - **Right rotation:** inserted in left subtree of left subtree.
  - **Left-Right rotation:** RR on subtree, then LL on whole tree.
  - **Right-Left rotation:** LL on subtree, then RR on whole tree.
- Applications:
  - In-memory sets/dictionaries
  - Database applications with frequent lookups, fewer insertions/deletions
  - Improved searching scenarios

### Question: What is B-tree? Applications?

- B-Tree is m-way tree used for disk access.
- Order `m` B-Tree has at most `m-1` keys and `m` children.
- Key advantage:
  - Many keys per node
  - Large key values
  - Small tree height
- Key properties:
  - All leaves at same height
  - Minimum degree `t` depends on disk block size
  - Except root, each node has at least `t-1` keys
  - Root has at least one key
  - Max keys per node = `2*t - 1`
  - Children count = key count + 1
  - Keys sorted ascending
  - Child between `k1` and `k2` stores keys between `k1` and `k2`
  - Grows/shrinks from root unlike BST
- Applications:
  - Disk data access in large databases
  - Faster data search
  - Multilevel indexing
  - Used by majority of servers

### Question: Define Segment Tree and applications

- Segment tree is binary tree storing intervals/segments.
- Nodes represent intervals.
- Used for:
  - Multiple range queries on array
  - Array element updates
- Key operations:
  - **Build tree**
  - **Update tree** (point/interval)
  - **Query tree** (range queries)
- Applications:
  - Intersecting rectangle pair listing
  - Pattern recognition and image processing
  - Range sum/product
  - Range max/min
  - Prefix sum/product
  - Computational geometry
  - Geographic information systems
  - Static/dynamic RMQ
  - Arbitrary segment storage

### Question: Define Trie and applications

- Trie = retrieval structure.
- Stores string set as sorted tree.
- Node has pointers equal to alphabet size.
- Supports prefix-based lookup (dictionary search).
- If alphabet is `a-z`, max pointers per node = 26.
- Also called:
  - Digital tree
  - Prefix tree
- Node connection key depends on Trie position.
- Time complexity:
  - Insert/find in **O(L)** where `L` is word length.
- Claimed advantages over BST and hashing:
  - Faster than BST
  - No hash computation
  - No collision handling (open addressing/chaining)
- Additional benefits:
  - Easy alphabetical printing
  - Efficient prefix search/autocomplete
- Main disadvantage:
  - High memory usage
  - Excess pointers per node
- Applications:
  - Search engine autocomplete/search
  - Genome analysis
  - Data analytics
  - Browser history
  - Spell checker

### Question: Define Red-Black Tree and applications

- Red-Black Tree is self-balancing BST.
- Invented by Rudolf Bayer (1972), called “symmetric binary B-trees”.
- Each node color: red or black.
- Balance guarantee:
  - No root-to-leaf path is more than twice another path.
- Stated comparison:
  - Similar to binary trees in storage format
  - Faster access advantage
- Can store any data representable as set of values.
- Rules:
  - Every node red or black
  - Root always black
  - No adjacent red nodes
  - Same number of black nodes from a node to descendant NULL paths
  - All leaf nodes black
- Applications:
  - Self-balancing BST libraries in C++/Java
  - Linux CPU scheduling
  - Reducing time complexity in K-mean clustering
  - MySQL table indexing for faster search/insert

### Question: Which data structures are used for LRU cache?

- LRU cache identifies least recently used element quickly.
- Uses:
  - **Queue** (implemented with doubly linked list)
    - Max size = cache size / available frames
    - Least recently used near front
    - Most recently used near rear
  - **HashMap**
    - Key = page number
    - Value = address of corresponding queue node

### Question: What is a heap data structure?

- Heap is a special tree-based non-linear structure.
- Tree is a **complete binary tree**.
- Complete binary tree:
  - All levels filled except maybe last
  - Last level filled from left
- Types:
  - **Max-Heap:** root has greatest value; recursively true for subtrees.
  - **Min-Heap:** root has smallest value; recursively true for subtrees.

---

## Data Structure Coding Interview Questions

### Question: Remove duplicates from a sorted array in place

- Input: `{1, 1, 1, 2, 3, 3, 6, 6, 7}`
- Output: `{1, 2, 3, 6, 7}`
- Explanation:
  - Unique elements are `1,2,3,6,7`.

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution{
public:
    //function that takes an array and its size as arguments
    int removeDuplicates(int a[],int n){
        int index=0;
        for(int i=1;i<n;i++) {
        
            if(a[i]!=a[index]) { //change index
                index++; //swap next line
                a[index]=a[i]; 
            } 
          }
          return index+1;
    }
};

int main()
{
    int T;
    //taking the number of test cases from user
    cin>>T;
    //running the loop for all test cases
    while(T--)
    {
        int N;
        //taking size input from user
        cin>>N;
        int a[N];
        //taking array input from user
        for(int i=0;i<N;i++)
        {
            cin>>a[i];
        }
        Solution ob;
        //calling the removeDuplicates in the Solution class
        int n = ob.removeDuplicates(a,N);
        //printing the array after removing duplicates
        for(int i=0;i<n;i++)
            cout<<a[i]<<" ";
            cout<<endl;
        }
}
```

- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

### Question: Zigzag traversal in a binary tree

- Output example: `[1, 3, 2, 4, 5, 6, 8, 7]`
- Explanation:
  - Traverse one level left-to-right, next level right-to-left.

```cpp
// Tree Node
struct Node {
    int data;
    Node* left;
    Node* right;
};

//Function to store the zigzag order traversal of a tree in a list.
    vector <int> zigZagTraversal(Node* root)
    {
     //creating two stacks for level traversals in both order
    	stack<Node*> st1;
    	stack<Node*> st2;
     //vector to store the zigzag traversal
    	vector<int> result;
    	
     //Initialize the first stack with the root element
    	st1.push(root);
    	
     //Iterate until either of the stack is not empty
    	while(!st1.empty() || !st2.empty()){
        //iterate until the first stack is not empty
    	    while(!st1.empty()){
    	        Node* temp=st1.top();
    	        st1.pop();
    	        result.push_back(temp->data);
    	        
    	        if(temp->left)
    	            st2.push(temp->left);
    	        if(temp->right)
    	            st2.push(temp->right);
    	    }
         //Iterate until the second stack is not empty
    	    while(!st2.empty()){
    	        Node* temp=st2.top();
    	        st2.pop();
    	        result.push_back(temp->data);
    	        
    	        if(temp->right)
    	            st1.push(temp->right);
    	        if(temp->left)
    	            st1.push(temp->left);
    	        
    	    }
    	}
    	return result;
    }
```

- Time Complexity: `O(n)`
- Space Complexity: `O(n)`

### Question: Sort a linked list of 0s, 1s, and 2s

- Input: `0->1->0->2->1->0->2->1`
- Output: `0->0->0->1->1->1->2->2`
- Explanation:
  - Count occurrences and rewrite nodes in order.

```cpp
//structure of the linked list
struct Node {
   int data;
   Node *left;
   Node *right;
}
//function take the head of the linked list as a parameter
void sortList(Node *head)
{
   //if linked list is empty then return back 
   if(head==NULL)
       return;
   else
   {
       Node *temp=head;
       Node *temp1=head;
       //to store count of 0s, 1s, and 2s
       int count0=0,count1=0,count2=0;
       //calculating the count of 0s, 1s, and 2s
       while(temp!=NULL)
       {
           if(temp->data==0)
               count0++;
           else if(temp->data==1)
               count1++;
           else
               count2++;
           temp=temp->next;
       }
       //iterating over count of 0s and filling the linked list
       while(count0!=0)
       {
           temp1->data=0;
           temp1=temp1->next;
           count0--;
       }
     //iterating over count of 1s and filling the linked list
       while(count1!=0)
       {
           temp1->data=1;
           temp1=temp1->next;
           count1--;
       }   
     //iterating over count of 2s and filling the linked list
       while(count2!=0)
       {
           temp1->data=2;
           temp1=temp1->next;
           count2--;
       }
   }
}
```

- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

### Question: Detect cycle in an undirected graph

- Input: `n = 4, e = 4, edges: 0-1, 1-2, 2-3, 3-1`
- Output: `Yes`
- Cycle: `1→2→3→1`

```cpp
//function to run dfs for a given node in the graph
  int dfs(int v,vector<int> adj[],vector<int> &visited,vector<int> &rec,int i,int parent){
        int ans=0;
        visited[i]=1;
        rec[i]=1;
        for(auto x : adj[i]){ 
            if(x!=parent) {
                if(rec[x]) 
                    return 1;
                ans=dfs(v,adj,visited,rec,x,i);
                if(ans) 
                   return 1;
            }
        }
        rec[i]=0;
        return 0;
    }
    // Function to detect cycle in an undirected graph.
    // it takes adjacency list representation as an argument
    bool isCycle(int v, vector<int> adj[]) {
        vector<int> visited(v,0),rec(v,0);
        int ans=0;
        for(int i=0;i<v;i++){
            if(visited[i]==0) 
                ans=dfs(v,adj,visited,rec,i,-1);
            if(ans) 
                return 1;
        }
        return 0;
    }
```

- Time Complexity: `O(V+E)`
- Space Complexity: `O(V)`

### Question: Convert infix expression to postfix expression

- Input: `a+b*(c^d)`
- Output: `abcd^*+`

```cpp
int prec(char c)
{
    if (c == '^')
        return 3;
    else if (c == '/' || c == '*')
        return 2;
    else if (c == '+' || c == '-')
        return 1;
    else
        return -1;
}
  public:
    // Function to convert an infix expression to a postfix expression.
    string infixToPostfix(string s) {
        stack<char> st; // For stack operations, we are using C++ built in stack
        string result;
 
        for (int i = 0; i < s.length(); i++) {
            char c = s[i];
 
            // If the scanned character is
            // an operand, add it to the output string.
            if ((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z')
            || (c >= '0' && c <= '9'))
                result += c;
 
            // If the scanned character is an
            // '(', push it to the stack.
            else if (c == '(')
                st.push('(');
 
            // If the scanned character is an ')',
            // pop and to output string from the stack
            // until an '(' is encountered.
            else if (c == ')') {
                while (st.top() != '(') {
                    result += st.top();
                    st.pop();
                }
                st.pop();
            }
 
            // If an operator is scanned
            else {
                while (!st.empty()
                   && prec(s[i]) <= prec(st.top())) {
                    if (c == '^' && st.top() == '^')
                        break;
                    else {
                        result += st.top();
                        st.pop();
                    }
                }
                st.push(c);
            }
        }
 
        // Pop all the remaining elements from the stack
        while (!st.empty()) {
            result += st.top();
            st.pop();
        }
 
        return result;
    }
```

- Time Complexity: `O(n)`
- Space Complexity: `O(n)`

### Question: Find maximum for every contiguous subarray of size `k`

- Input: `N = 9, K = 3, arr = {1, 2, 3, 1, 4, 5, 2, 3, 6}`
- Output: `{3, 3, 4, 5, 5, 5, 6}`
- Explanation:
  - For first subarray `{1,2,3}`, max is `3`, similarly for each window.

```cpp
//function to find maximum in each subarray using sliding window approach
vector<int> max_of_subarrays(vector<int> arr, int n, int k){
        int i=0,j=0;
        deque<int> dq;
        dq.push_front(i++);
        while(i<k)
        {
            while(!dq.empty()&&arr[dq.back()]<=arr[i])
            dq.pop_back();
            dq.push_back(i++);
        }
        vector<int> ans;
        while(i<n)
        {
            ans.push_back(arr[dq.front()]);
            while(!dq.empty()&&j>=dq.front())
            {
                dq.pop_front();
                
            }
            j++;
             while(!dq.empty()&&arr[dq.back()]<=arr[i])
            dq.pop_back();
            dq.push_back(i++);
        }
        ans.push_back(arr[dq.front()]);
        return ans;
    
    }
```

- Time Complexity: `O(n)`
- Space Complexity: `O(k)`

### Question: Merge two sorted BSTs

- Input:
  - First BST root `7` with children `5`, `9`
  - Second BST root `4` with children `3`, `12`
- Output: `3 4 5 6 7 9 12`

```cpp
//Function to return a list of integers denoting the node 
//values of both the BST in a sorted order.
    void inorder(Node*root,vector<int>&v){
        if(root==NULL)
            return;
        inorder(root->left,v);
        v.push_back(root->data);
        inorder(root->right,v);
    }
    vector<int> merge(vector<int>v1,vector<int>v2){
        vector<int>v;
        int n1=v1.size(),n2=v2.size(),i=0,j=0;
        while(i<n1&&j<n2){
            if(v1[i]>v2[j]){
                v.push_back(v2[j]);
                j++;
            }
            else{
                v.push_back(v1[i]);
                i++;
            }
        }
        while(i<n1){
            v.push_back(v1[i]);
            i++;
        }
        while(j<n2){
            v.push_back(v2[j]);
            j++;
        }
        return v;
    }
    vector<int> merge(Node *root1, Node *root2)
    {
       vector<int>v1,v2;
       inorder(root1,v1);
       inorder(root2,v2);
       return merge(v1,v2);
    }
```

- Time Complexity: `O(m+n)`
- Space Complexity: `O(height of first tree + height of second tree)`

### Question: Print all unique rows of a matrix

- Input:
```text
{{1, 1, 1, 0, 0},
 {0, 1, 0, 0, 1},
 {1, 0, 1, 1, 0},
 {0, 1, 0, 0, 1},
 {1, 1, 1, 0, 0}}
```
- Output:
```text
{{1, 1, 1, 0, 0},
 {0, 1, 0, 0, 1},
 {1, 0, 1, 1, 0}}
```

```cpp
vector<vector<int>> uniqueRow(int M[MAX][MAX],int row,int col)
{
set<vector<int>> st;
vector<vector<int>> v;

for(int i=0; i<row; i++) {
    vector<int> v1;
    for(int j=0; j<col; j++) {
        v1.push_back(M[i][j]);
    }
    if(st.count(v1) == 0) {
         v.push_back(v1);
         st.insert(v1);
    }
}

return v;
}
```

- Time Complexity: `O(ROW x COL)`
- Space Complexity: `O(ROW)`

### Question: Find number of subarrays with product less than `K`

- Input: `arr = [1, 6, 2, 3, 2, 1], k = 12`
- Output: `11`

```cpp
int numSubarrayProductLessThanK(vector<int>& nums, int k) {
        int ans=0;
        int pdt=1;
        int left=0,right=0;
        while(right<=nums.size()-1){
            
            pdt*=nums[right];
            while(pdt>=k and left<nums.size()){
                pdt/=nums[left];
                left++;
                
            }
            if(right-left>=0)
            ans+=right-left+1;//since on adding a new element new subarrays formed is r-i+1;
            right++;
            
        }
        return ans;
    }
```

- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

### Question: Find increasing subsequence of length 3 with highest product

- Input: `n = 8, arr = {6, 7, 10, 1, 2, 3, 11, 12}`
- Output: `{10, 11, 12}`
- Explanation:
  - Increasing elements `10, 11, 12` give highest product among size-3 subsequences.

```cpp
 vector<int> maxProductSubsequence(int *a , int n) 
    { 
        set<int> s;
        long long largestOnLeft[n];
        for(int i=0;i<n;i++)
        {   
            s.insert(a[i]);
            auto it=s.lower_bound(a[i]);
            if(it==s.begin())
            {
                largestOnLeft[i]=-1;
                continue;
            }
            it--;
            largestOnLeft[i]=*it;
        }
        int m=0;
        long long p=INT_MIN;
        vector<int> result(3);
        result[0]=-1;
        for(int i=n-1;i>=0;i--)
        {   
          if(a[i]>=m){
          m=a[i];}
          else
          {
              if(largestOnLeft[i] !=-1)
              {
                  if(largestOnLeft[i]*a[i]*m >p)
                  {
                      p=largestOnLeft[i]*a[i]*m;
                      result[0]=largestOnLeft[i];
                      result[1]=a[i];
                      result[2]=m;
                  }
              }
          }
        }
        return v;
    }
```

- Time Complexity: `O(nlog(n))`
- Space Complexity: `O(n)`

### Question: Implement quicksort on doubly linked list

- Input: `8<->10<->1<->7<->6`
- Output: `1<->6<->7<->8<->10`

```cpp
class Solution{
public:
    Node* partition(Node *l, Node *h){
        //Your code goes here
        Node*temp = h;
        Node*tt = l;
        Node*first = l;
        
        while(tt != h){
              if(tt->data <= temp->data){
                  swap(first->data, tt->data);
                  first = first->next;
              }
              tt = tt -> next;
        }
        swap(first-> data, h->data);
        return first;
    
    }
};

void _quickSort(struct Node* l, struct Node *h)
{
    if (h != NULL && l != h && l != h->next)
    {
        Solution ob;
        struct Node *p = ob.partition(l, h);
        _quickSort(l, p->prev);
        _quickSort(p->next, h);
    }
}
 
void quickSort(struct Node *head)
{
    struct Node *h = lastNode(head);
    _quickSort(head, h);
}
```

- Time Complexity:
  - Worst case: `O(n^2)` (already sorted list)
  - Best/average: `O(nlog(n))`
- Space Complexity: `O(n)`

### Question: Connect nodes at same level in binary tree

- Input tree has nodes:
  - `100`
  - `13`, `15`
  - `14`, `1`, `20`
- Output level links:
  - `100 -> NULL`
  - `13 -> 15 -> NULL`
  - `14 -> 1 -> 20 -> NULL`

```cpp
class Solution
{
    public:
    //Function to connect nodes at the same level.
    void connect(Node *p)
    {
       map<int,vector<Node *> > m;
       queue<Node *> q;
       queue<int> l;
       q.push(p);
       l.push(0);
       while(!q.empty())
       {
           Node *temp=q.front();
           int level=l.front();
           q.pop();
           l.pop();
           m[level].push_back(temp);
           if(temp->left!=NULL)
           {
               q.push(temp->left);
               l.push(level+1);
           }
           if(temp->right!=NULL)
           {
               q.push(temp->right);
               l.push(level+1);
           }
       }
       for(map<int,vector<Node *> > ::iterator it=m.begin();it!=m.end();it++)
       {
           vector<Node *> temp1=it->second;
           for(int i=0;i<temp1.size()-1;i++)
           {
               temp1[i]->nextRight=temp1[i+1];
           }
           temp1[temp1.size()-1]->nextRight=NULL;
       }
    }
};
```

- Time Complexity: `O(n)`
- Space Complexity: `O(n)`

### Question: Number of structurally unique BSTs

- Input: `N = 3`
- Output: `5`
- Explanation:
  - For `N=3`, five unique BST structures are possible.

```cpp
class Solution
{
    public:
     //function to calculate binomial coefficient C(n,k)
    long long int binomialCoefficient(long long int n, long long int k)
    {
        long long int res = 1;
        if (k > n - k)
            k = n - k;
    
        for (long long int i = 0; i < k; ++i)
        {
            res *= (n - i);
            res /= (i + 1);
        }
     
        return res;
    }
     
   //function to calculate Nth Catalan Number  
    long long int catalanNumber(long long in n)
    {
        // Calculate value of 2nCn
        long long int C = binomialCoefficient(2*n, n);
    
        // return 2nCn/(n+1)
        return C/(n+1);
    }
    
    //Function to return the total number of possible unique BST. 
    long long int numOfUniqueBinarySearchTrees(int n) 
    {
         // find nth catalan number
        long long int countOfUniqueBinarySearchTrees = catalanNumber(n);
     
        // return nth catalan number
        return countOfUniqueBinarySearchTrees;
    }
};
```

- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

### Question: Implement LRU Cache

```cpp
class LRUCache
{
    private:
    class node_t {
        public:
        int key;
        int value;
        node_t * next;
        node_t * prev;
    };
    
    int cap;
    node_t head;
    unordered_map<int, node_t*> tbl;
    
    void remove_node(node_t * node) {
        node->next->prev = node->prev;
        node->prev->next = node->next;
    }
    void add_node(node_t * node) {
        node->next = head.next;
        node->prev = &head;
        head.next = node;
        node->next->prev = node;
    }
    public:
    //Constructor for initializing the cache capacity with the given value.
    LRUCache(int cap): cap(cap)
    {
        // code here
        head.prev = &head;
        head.next = &head;
    }
    
    //Function to return value corresponding to the key.
    int get(int key)
    {
        // your code here
        unordered_map<int, node_t*>::iterator it = tbl.find(key);
        if(it==tbl.end())
            return -1;
        remove_node(it->second);
        add_node(it->second);
        return it->second->value;
    }
    
    //Function for storing key-value pair.
    void set(int key, int value)
    {
        // your code here   
        unordered_map<int, node_t*>::iterator it = tbl.find(key);
        if(it!=tbl.end())
        {
            remove_node(it->second);
            add_node(it->second);
            it->second->value = value;
        }
        else {
            node_t * node = new node_t;
            node->key = key;
            node->value = value;
            add_node(node);
            tbl[key] = node;
            if(tbl.size()>cap) {
                auto * old_node = head.prev;
                tbl.erase(old_node->key);
                remove_node(old_node);
                delete old_node;
            }
        }
    }
};
```

- Time Complexity: `O(1)` to get an element
- Space Complexity: `O(n)`

### Question: Check duplicate elements within given distance

- Input: `arr = {1, 2, 3, 4, 2, 1, 2}, range = 3`
- Output: `True`

```cpp
class Solution {
    public:
    
    bool checkDuplicatesWithinRange(vector<int> arr, int range)
    {
        // Creating an empty hashset
        unordered_set<int> myset;
     
        // Traversing the input array
        for (int i = 0; i < arr.size(); i++)
        {
            // If already present in hashset, then we found a duplicate within range distance
            if (myset.find(arr[i]) != myset.end())
                return true;
     
            // Add this item to hashset
            myset.insert(arr[i]);
     
            // Remove the range+1 distant item from the hashset
            if (i >= range)
                myset.erase(arr[i-range]);
        }
        return false;
    }
};
```

- Time Complexity: `O(n)`
- Space Complexity: `O(n)`

### Question: Recursive height of binary tree in Java

```java
public class Node{
     int data;
     Node left;
     Node right;
 }
```

```java
int heightOfBinaryTree(Node node)  
{ 
    if (node == null) 
        return 0; // If node is null then height is 0 for that node.
    else 
    { 
        // compute the height of each subtree
        int leftHeight = heightOfBinaryTree(node.left); 
        int rightHeight = heightOfBinaryTree(node.right);     
        //use the larger among the left and right height and plus 1 (for the root)
        return Math.max(leftHeight, rightHeight) + 1; 
    } 
}
```

### Question: Count nodes in a binary tree in Java

```java
int countNodes(Node root)
{
    int count =  1;             //Root itself should be counted
    if (root ==null)
        return 0;
    else
    {
        count += countNodes(root.left);
        count += countNodes(root.right);
        return count;
    }
}
```

### Question: Print left view of a binary tree

- Main idea:
  - Preorder traversal with level information.
  - If level visited first time, store node in hashmap.
  - Left view = first node at every level.
- Final output obtained by traversing map.

```java
import java.util.HashMap;

//to store a Binary Tree node
class Node
{
    int data;
    Node left = null, right = null;

    Node(int data) {
        this.data = data;
    }
}
public class Main
{
    // traverse nodes in pre-order way
    public static void leftViewUtil(Node root, int level, HashMap<Integer, Integer> map)
    {
        if (root == null) {
            return;
        }

        // if you are visiting the level for the first time
        // insert the current node and level info to the map
        if (!map.containsKey(level)) {
            map.put(level, root.data);
        }

        leftViewUtil(root.left, level + 1, map);
        leftViewUtil(root.right, level + 1, map);
    }

    // to print left view of binary tree
    public static void leftView(Node root)
    {
        // create an empty HashMap to store first node of each level
        HashMap<Integer, Integer> map = new HashMap<>();

        // traverse the tree and find out the first nodes of each level
        leftViewUtil(root, 1, map);

        // iterate through the HashMap and print the left view
        for (int i = 0; i <map.size(); i++) {
            System.out.print(map.get(i) + " ");
        }
    }

    public static void main(String[] args)
    {
        Node root = new Node(4);
        root.left = new Node(2);
        root.right = new Node(6);
        root.left.left = new Node(1);
        root.left.left = new Node(3);
        root.right.left = new Node(5);
        root.right.right = new Node(7);
        root.right.left.left = new Node(9);

        leftView(root);
    }
}
```

### Question: Number of islands in 2D grid

- Grid:
  - `'1'` = land
  - `'0'` = water
- Islands are connected vertically or horizontally.
- Boundary edges assumed surrounded by water.
- Constraints:
  - `m == grid.length`
  - `n == grid[i].length`
  - `1 <= m, n <= 300`
  - `grid[i][j]` is only `'0'` or `'1'`
- Example input:
```text
[
[“1” , “1” , “1” , “0” , “0”],
[“1” , “1” , “0” , “0” , “0”],
[“0” , “0” , “1” , “0” , “1”],
[“0” , “0” , “0” , “1” , “1”]
]
```
- Output: `3`

```java
class Main {
    public int numberOfIslands(char[][] grid) {
        if(grid==null || grid.length==0||grid[0].length==0)
            return 0;

        int m = grid.length;
        int n = grid[0].length;

        int count=0;
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(grid[i][j]=='1'){
                    count++;
                    mergeIslands(grid, i, j);
                }
            }
        }

        return count;
    }

    public void mergeIslands(char[][] grid, int i, int j){
        int m=grid.length;
        int n=grid[0].length;

        if(i<0||i>=m||j<0||j>=n||grid[i][j]!='1')
            return;

        grid[i][j]='X';

        mergeIslands(grid, i-1, j);
        mergeIslands(grid, i+1, j);
        mergeIslands(grid, i, j-1);
        mergeIslands(grid, i, j+1);
    }
}
```

### Question: What is topological sorting in a graph?

- Topological sorting = linear ordering of vertices such that for every directed edge `i -> j`, `i` comes before `j`.
- Only possible for **DAG (Directed Acyclic Graph)**.
- Applications:
  - Job scheduling with dependencies
  - Spreadsheet formula cell evaluation order
  - Compilation task order in make files
  - Data serialization
  - Symbol dependency resolution in linkers

```java
// V - total vertices
// visited - boolean array to keep track of visited nodes
// graph - adjacency list.
// Main Topological Sort Function. 
void topologicalSort() 
{ 
    Stack<Integer> stack = new Stack<Integer>(); 

    // Mark all the vertices as not visited 
    boolean visited[] = new boolean[V]; 
    for (int j = 0; j < V; j++){ 
        visited[j] = false; 
    }
    // Call the util function starting from all vertices one by one 
    for (int i = 0; i < V; i++) 
        if (visited[i] == false) 
            topologicalSortUtil(i, visited, stack); 

    // Print contents of stack -> result of topological sort
    while (stack.empty() == false) 
        System.out.print(stack.pop() + " "); 
} 

// A helper function used by topologicalSort
void topologicalSortUtil(int v, boolean visited[], 
                         Stack<Integer> stack) 
{ 
    // Mark the current node as visited. 
    visited[v] = true; 
    Integer i; 

    // Recur for all the vertices adjacent to the current vertex 
    Iterator<Integer> it = graph.get(v).iterator(); 
    while (it.hasNext()) { 
        i = it.next(); 
        if (!visited[i]) 
            topologicalSortUtil(i, visited, stack); 
    } 

    // Push current vertex to stack that saves result 
    stack.push(new Integer(v)); 
}
```

---

## Python DSA Interview Questions

### Question: What Python features reduce code complexity in DSA solutions?

- Dynamic typing reduces boilerplate.
- Built-in data structures (`list`, `set`, `dict`) simplify logic.
- List comprehensions allow compact loops.
- Functions and modules help organize code.
- Result: shorter and cleaner DSA solutions.

### Question: What role do Python built-ins play in DSA interviews?

- Built-ins like `sort`, `min`, `max`, `sum` simplify solutions.
- They reduce code length and improve readability.
- Candidate must know their time complexity.
- Interviewers expect justification for using them.

### Question: Why are optimization follow-ups more important than initial solution?

- Initial solution shows problem understanding.
- Optimization shows deeper thinking.
- Interviewers evaluate time/space reduction ability.
- Reflects real engineering problem handling.
- Strong candidates clearly explain why optimized solution is better.

### Question: What patterns do frequently asked DSA questions follow?

- Common patterns:
  - Sliding window
  - Two pointers
  - Hashing
  - Recursion
- Interviewers expect mapping question to known pattern.
- Early pattern recognition avoids random trial-and-error.
- Leads to focused and clean solution.
- Shows structured practice.

---

## Coding Problems Progress Snapshot

- `0/4` Easy Problems
  - Arrays
  - Stacks And Queues
  - Graph Data Structure & Algorithms
  - Tree Data Structure
- Easy problems listed:
  - Max Sum Contiguous Subarray
    - Easy
    - 33.39 Mins
    - +4
    - Solve
  - Evaluate Expression
    - Easy
    - 32.46 Mins
    - Solve
  - Level Order
    - Easy
    - 29.55 Mins
    - Solve
  - Inorder Traversal
    - Easy
    - 32.0 Mins
    - Solve
- `0/2` Intermediate Problems
  - Linked Lists
  - Graph Data Structure & Algorithms
- `0/1` Advanced Problems
  - Graph Data Structure & Algorithms
- View All Problems

---

## Data Structure MCQ

### Question: Which of the following is a non-linear data structure?

- Array
- Linked List
- Queue
- Tree

**Answer:** Tree

### Question: Which of the following data structures is linear?

- Graph
- AVL Tree
- Red-Black Tree
- Stack

**Answer:** Stack

### Question: Which data structure is used for implementing recursion?

- Array
- Stack
- Queue
- Linked List

**Answer:** Stack

### Question: Which of the following data structures are indexed structures?

- Queue
- Trees
- Linear Arrays
- None of the above

**Answer:** Linear Arrays

### Question: Stack data structure cannot be used for

- Expression Evaluation in Postfix Form
- String Reversal
- Recursion Implementation
- Resource Allocation and Scheduling

**Answer:** Resource Allocation and Scheduling

### Question: Which data structure is preferred in database implementation?

- B-Tree
- Binary Search Tree
- AVL Tree
- B+- Tree

**Answer:** B+- Tree

### Question: How can memory be saved for color in Red-Black tree?

- Using least significant bit of one node pointer
- Another array with colors
- Keep color data in node structure
- Use both negative and positive numbering

**Answer:** Using least significant bit of one node pointer

### Question: Best data structure for dictionary word search

- Binary Search Tree
- Graph
- N-ary tree
- Trie

**Answer:** Trie

### Question: True statement about B-tree split frequency

- Less frequent split if order is large
- More frequent split if order is large
- More frequent split if order is small
- Less frequent split if order is small

**Answer:** Less frequent split if order is large

### Question: Worst-case time complexity of inserting `n` elements into empty sorted linked list

- `O(n)`
- `O(log(n))`
- `O(nlog(n))`
- `O(n^2)`

**Answer:** `O(n^2)`

### Question: Which data structure cannot store non-homogeneous elements?

- Arrays
- Records
- Pointers
- Stacks

**Answer:** Arrays

### Question: Directed graph is _______ if each vertex can reach every other vertex

- Weakly connected
- Strongly connected
- Tightly connected
- Linearly connected

**Answer:** Strongly connected

### Question: Traversal where descendants are processed before adjacent vertex

- BFS
- DFS
- Level Order
- Width first

**Answer:** DFS

### Question: In circular queue, REAR would be

- `REAR = REAR + 1`
- `REAR = (REAR + 1) % (QUEUE_SIZE+1)`
- `REAR = (REAR + 1) % (QUEUE_SIZE)`
- `REAR = (REAR - 1) % (QUEUE_SIZE-1)`

**Answer:** `REAR = (REAR + 1) % (QUEUE_SIZE)`

### Question: Which statement is true?

- Statement i): With singly linked and circular list, backward traversal is not possible.
- Statement ii): In singly linked list, predecessor search requires traversal from first node.
- Options:
  - i only
  - ii only
  - both i and ii
  - None of the above

**Answer:** both i and ii

### Question: Binary search needs no more than ______ comparisons

- `(log2n) + 1`
- `logn`
- `(logn) + 1`
- `log2n`

**Answer:** `(log2n) + 1`

### Question: Properties of binary tree

- First subset is left subtree
- Second subset is right subtree
- Root cannot contain NULL
- Right subtree can be empty

**Answer:** Right subtree can be empty

### Question: “Arrays are best data structures” is true in which scenario?

- Size/data constantly changing
- Relatively permanent data collections
- Both A and B
- None of the above

**Answer:** Relatively permanent data collections

### Question: Which snippet converts decimal to binary?

A)
```java
public void convertBinary(int num)
{
int bin[] = new int[50];
int index = 0;
while(num > 0)
{
bin[index++] = num%2;
num = num/2;
}
for(int i = index-1;i >= 0;i--)
{
System.out.print(bin[i]);
}
}
```

B)
```java
public void convertBinary(int num)
 {
     int bin[] = new int[50];
     int index = 0;
     while(num > 0)
     {
         bin[++index] = num/2;
         num = num%2;
     }
     for(int i = index-1;i >= 0;i--)
     {
         System.out.print(bin[i]);
     }
  }
```

C)
```java
public void convertBinary(int num)
{
     int bin[] = new int[50];
     int index = 0;
     while(num > 0)
     {
         bin[index++] = num/2;
         num = num%2;
     }
     for(int i = index-1;i >= 0;i--)
     {
         System.out.print(bin[i]);
     }
}
```

D)
```java
public void convertBinary(int num)
{
     int bin[] = new int[50];
     int index = 0;
     while(num > 0)
     {
       bin[++index] = num%2;
       num = num/2;
     }
     for(int i = index-1;i >= 0;i--)
     {
       System.out.print(bin[i]);
     }
}
```

- Answer options:
  - A
  - B
  - C
  - D

**Answer:** A

### Question: Final stack after operations

- Operations:
  - `Push(a,s);`
  - `Push(b,s);`
  - `Pop(s);`
  - `Push(c,s);`
- Options:
  - abc
  - ac
  - acb
  - b

**Answer:** ac

### Question: Dijkstra’s algorithm cannot be applied on

- Directed and weighted graphs
- Graphs with negative weight function
- Unweighted graphs
- Undirected and unweighted graphs

**Answer:** Graphs with negative weight function

---

## Conceptual Revision Questions (Additional)

### Question: What is a data structure and why is it important?

- **Definition:** Organizing and storing data for efficient use.
- Defines:
  - Memory arrangement of elements
  - Operation behavior (store/access/search/update/delete)
- Without proper structures:
  - Programs become slow
  - Complexity increases
  - Manageability decreases
- Main importance:
  - Performance
- Different problems need different storage methods.
- Example:
  - Search in unsorted list takes more time than sorted structure.
- Correct structure choice can reduce:
  - Execution time
  - Memory usage
- Improves:
  - Code cleanliness
  - Organization
  - Maintainability
- Real systems depending on efficient structures:
  - Databases
  - Operating systems
  - File systems
  - Search engines
- Interview signal:
  - Foundation understanding of CS problem solving
  - Ability to build scalable, efficient, reliable software

### Question: Difference between linear and nonlinear structures?

- **Linear**
  - Sequential arrangement
  - One previous and one next (except ends)
  - Examples: arrays, linked lists, stacks, cues
  - Easy to understand and implement
  - Good for ordered processing
  - Insert/delete can be slow in some cases
- **Nonlinear**
  - Non-sequential storage
  - Hierarchical/network links
  - Examples: trees, graphs
  - One element can connect to many elements
  - Good for complex relationships:
    - File systems
    - Organization charts
    - Social networks
- Interview focus:
  - How organization affects performance and problem-solving

### Question: What is an array and its pros/cons?

- **Definition:** Linear structure storing same-type elements in continuous memory.
- Index-based direct access.
- Very fast for reads/access.
- Advantages:
  - Simple
  - Broad language support
  - Cache-friendly memory access
- Limitations:
  - Often fixed size
  - Inflexible for dynamic growth/shrink
  - Mid insert/delete costly (shifts needed)
  - Potential memory waste if over-allocated
- Not always ideal for dynamic data.
- Interview focus: performance trade-offs.

### Question: What is a linked list and how is it different from array?

- **Definition:** Linear structure of nodes.
- Node has:
  - Data
  - Reference to next node
- Non-contiguous memory.
- Main advantage:
  - Dynamic memory allocation
- Easy insert/delete without shifting.
- Slower access than arrays (must traverse from head).
- Search slower due to sequential traversal.
- Extra memory needed for references.
- Choice depends on problem constraints.
- Interview focus:
  - Memory usage
  - Performance
  - Real-world application mapping

### Question: What is a stack and how does it work?

- **Definition:** Linear structure using **LIFO**.
- Last inserted element removed first.
- Example: pile of plates.
- Operations:
  - Push (insert)
  - Pop (remove)
- Both at one end: top.
- Simple to implement/manage.
- Applications:
  - Function call stack
  - Undo/redo
  - Expression evaluation
  - Compiler syntax parsing
- Limitation:
  - No random access
  - Only top element directly accessible
- Interview focus:
  - Data flow control
  - Execution order management

### Question: What is a Q and how is it different from stack?

- **Definition:** Linear structure using **FIFO**.
- First inserted element removed first.
- Example: ticket line.
- Operations:
  - Insert at rear (`uncq`)
  - Remove at front (`DQ`)
- Provides fairness by arrival order.
- Difference:
  - Stack removes most recent
  - Q removes earliest
- Uses:
  - Task scheduling
  - Shared resource management
  - Request handling
  - OS scheduling
  - Printer queue
  - Network data handling
- Interview focus:
  - Ordering logic
  - Real-world usage

### Question: What is a circular Q and why used?

- Circular Q connects last position to first.
- Reuses freed front space after dequeues.
- Solves array-based normal queue wasted-space issue.
- Rear wraps to beginning when space is free.
- Benefits:
  - Better memory efficiency
  - Good for fixed-size buffers
- Uses:
  - Real-time systems
  - Data stream buffering
  - CPU scheduling
- Interview focus:
  - Memory optimization
  - Efficient handling

### Question: What is a DQ and difference from Q?

- DQ = double-ended Q.
- Insert/delete allowed at both front and rear.
- Normal Q is one-directional.
- Higher flexibility.
- Useful when both-end access is needed.
- Mentioned applications:
  - Sliding window problems
  - Catching mechanisms
  - Task scheduling
- Can behave as stack or queue.
- Interview focus:
  - Advanced queue variations
  - Correct structure selection

### Question: What is a tree and where is it used?

- **Definition:** Nonlinear hierarchical structure.
- Components:
  - Nodes
  - Edges
- Top node: root.
- Nodes may have one or more children.
- No-child nodes: leaves.
- Fits real-world parent-child relationships.
- Examples:
  - File systems
  - Org charts
  - XML
  - HTML
- Advantage:
  - Efficient search and organization
- Can outperform linear structures for lookup.
- Sorted tree variants improve performance further.
- Used in:
  - Databases
  - Compilers
  - Search engines
- Interview focus:
  - Hierarchical representation
  - Practical importance

### Question: What is binary tree vs general tree?

- Binary tree:
  - Max two children per node
  - Left child and right child
  - Easier processing and analysis
- General tree:
  - Any number of children
  - More flexible but harder traversal/management
- Binary tree strictness simplifies operations.
- Common uses:
  - Search/sort
  - BSTs for fast updates/lookups
  - Expression trees in compilers
- Interview focus:
  - Constraints improving simplicity/performance

### Question: What is BST and why important?

- BST = binary tree with order rule:
  - Left subtree values smaller
  - Right subtree values greater
- Efficient searching:
  - Can eliminate half of remaining nodes each step
- Faster than linear structures for search.
- Supports efficient insert/delete while keeping sorted order.
- Useful where frequent updates + fast lookups are needed.
- Interview focus:
  - How ordering drives performance

### Question: What is tree traversal and why important?

- Tree traversal visits all nodes in defined order.
- Required because trees are nonlinear.
- Methods include:
  - Root-first
  - Child-first
  - Level-order
- Different methods produce different visit orders.
- Needed for:
  - Search
  - Copy
  - Delete
  - Evaluation
- Example:
  - Expression tree evaluation depends on traversal order.
- Interview focus:
  - Essential processing techniques for hierarchical data

### Question: What is heap and where used?

- Heap = special tree-based structure with ordering rule.
- Parent is always larger/smaller than children based on type.
- Max heap: parent greater.
- Min heap: parent smaller.
- Usually array implementation.
- Tree logic maintained via index calculations.
- Benefits:
  - Memory efficient
  - Fast operations
  - Root always holds highest/lowest priority
- Uses:
  - Priority cues
  - Heap sort (mentioned as “heap [snorts] sort”)
  - CPU scheduling
  - Task management
  - Graph algorithms
- Interview focus:
  - Priority-based retrieval and processing

### Question: What is graph and difference from tree?

- Graph:
  - Nonlinear structure
  - Vertices + edges
  - Flexible relationships
- Unlike tree:
  - No mandatory single root
  - Can include cycles
  - Can be directed or undirected
- Tree described as special graph:
  - No cycles
  - Exactly one path between nodes
  - Hierarchical
- Graphs are more powerful but more complex.
- Uses:
  - Social networks
  - Maps
  - Recommendation systems
  - Network routting
- Interview focus:
  - Complex relationship modeling

### Question: What is graph traversal and why important?

- Graph traversal = systematic node visiting.
- More complex than tree traversal due to cycles/multiple paths.
- Goal:
  - Visit each node
  - Avoid infinite loops
- Importance:
  - Search
  - Connection analysis
  - Path finding
  - Cycle detection
- Uses visited-node tracking.
- Applications:
  - Navigation
  - Network analysis
  - Dependency resolution
- Foundation for advanced algorithms.
- Interview focus:
  - Safe and efficient exploration

### Question: Difference between breath first search and depth first search?

- Two common traversal methods.
- Bread first search:
  - Explore neighbors level by level.
  - Useful for shortest path in unweighted graph.
- Depth first search:
  - Go deep on one path, then backtrack.
  - Useful for cycle detection/topological sorting.
- Choosing correct method is problem-dependent.
- Interview focus:
  - Strategy selection and algorithm behavior understanding

### Question: What is hash table and how it works?

- Stores key-value pairs.
- Fast insertion/deletion/search.
- Uses hash function to map key to index.
- Hash code identifies bucket.
- Value stored in bucket.
- Lookup uses same hash function.
- Collision challenge:
  - Different keys same hash code
- Collision handling:
  - Chaining
  - Open addressing
- Used in:
  - Databases
  - Caching
  - Compiler symbol tables
- Interview focus:
  - Faster access versus linear search

### Question: What is collision handling in hash table?

- Handles same-index mapping of multiple keys.
- Required because same memory slot cannot directly hold multiple keys without method.
- Methods:
  - **Chaining**
    - Bucket stores list of key-value pairs.
    - Multiple keys in same bucket list.
    - Simple/effective, but depends on list length.
  - **Open addressing**
    - On collision, probe another bucket by sequence.
    - Place value in next available location.
- Poor collision handling can degrade `O(1)` to `O(n)`.
- Interview focus:
  - Hash internals and optimization

### Question: What is priority Q and how implemented?

- Priority Q assigns priority to each element.
- Higher priority removed first, not insertion order.
- Normal queue is FIFO; priority queue is importance-based.
- Example: emergency room triage.
- Common implementation:
  - Heap
- Heap supports efficient insert/delete and quick priority access.
- Uses:
  - CPU scheduling
  - Pathfinding
  - Event-driven simulation
- Interview focus:
  - Priority processing and system design

### Question: What is sorting algorithm and why important?

- Sorting algorithm arranges data (ascending/descending).
- Sorted data is easier to search/analyze/process.
- Many systems rely on sorted data:
  - Databases
  - Search engines
- Different sorting algorithms optimize different goals:
  - Speed
  - Memory
  - Simplicity
- Selection depends on data size and application needs.
- Interview focus:
  - Sorting in optimization and problem solving