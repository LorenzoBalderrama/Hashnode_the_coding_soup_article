---
title: "Algorithms and Data Structures in Swift"
datePublished: Wed Jun 21 2023 11:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clj5lsf7h0q82ojnvdgijdm6j
slug: algorithms-and-data-structures-in-swift
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687035705974/c1f16972-f18e-49c3-80ec-078791af2b8a.png
tags: algorithms, swift, data-structures, swiftui, thecodingsoup

---

---

Algorithms and data structures play a pivotal role in software development. Swift simplifies their implementation with its high-level abstractions. This article will provide a more in-depth understanding of implementing common algorithms and data structures in Swift.

## **What are Algorithms?**

An algorithm is a predefined set of instructions designed to solve a specific problem. In computer programming, algorithms provide solutions to problems by manipulating data in various ways. The efficiency of an algorithm is primarily judged by its time and space complexity.

## **Algorithms in Swift**

While Swift's standard library provides many methods to perform routine tasks, a deeper understanding of these core algorithms can lead to optimized problem-solving. Let's explore some of these algorithms:

### **1\. Sorting Algorithms**

Sorting algorithms arrange elements of a list in a specific order. Swift has a built-in `sort` method, but let's dive deeper with a step-by-step implementation of the bubble sort algorithm:

```swift
func bubbleSort(_ array: [Int]) -> [Int] {
    var arr = array // A copy of the array is made to avoid mutating the original array
    for _ in 0..<arr.count { // Outer loop runs for each element in the array
        for j in 1..<arr.count { // Inner loop also iterates over each element
            if arr[j-1] > arr[j] { // If the current element is greater than the next
                let temp = arr[j-1] // Swap the elements
                arr[j-1] = arr[j]
                arr[j] = temp
            }
        }
    }
    return arr // Return the sorted array
}
```

### **2\. Searching Algorithms**

Searching algorithms help locate an element in a data structure. Linear search and binary search are two common algorithms:

* **Linear Search**: A simple search algorithm that checks every element:
    

```swift
func linearSearch<T: Equatable>(_ array: [T], _ object: T) -> Int? {
    for (index, obj) in array.enumerated() where obj == object {
        // The enumerated() function provides the index and value for each element in the array.
        // 'where obj == object' is a condition that stops the loop when the object is found.
        return index // The index of the found object is returned.
    }
    return nil // If the object isn't found, nil is returned.
}
```

* **Binary Search**: A faster algorithm that works on sorted arrays:
    

```swift
func binarySearch<T: Comparable>(_ array: [T], key: T, range: Range<Int>) -> Int? {
    if range.lowerBound >= range.upperBound {
        // This condition checks if the entire array or subarray has been searched
        return nil // If yes, and the element hasn't been found, nil is returned
    } else {
        let midIndex = range.lowerBound + (range.upperBound - range.lowerBound) / 2
        // midIndex calculates the index of the middle element
        if array[midIndex] > key {
            // If the middle element is larger than the key, search the left subarray
            return binarySearch(array, key: key, range: range.lowerBound ..< midIndex)
        } else if array[midIndex] < key {
            // If the middle element is smaller than the key, search the right subarray
            return binarySearch(array, key: key, range: midIndex + 1 ..< range.upperBound)
        } else {
            return midIndex // If the middle element is equal to the key, return its index
        }
    }
}
```

## **Data Structures in Swift**

Data structures organize and store data for efficient access and modification. They define the relationship between data, and the operations that can be performed on them.

### **1\. Arrays**

Arrays store an ordered list of elements, which can be accessed via their index:

```swift
var numbers = [1, 2, 3, 4, 5] // An array of numbers
print(numbers[0]) // Accesses the element at index 0
numbers.append(6) // Adds an element to the end of the array
```

### **2\. Sets**

A set is an unordered collection of unique elements:

```swift
var uniqueNumbers = Set<Int>() // A set of integers
uniqueNumbers.insert(1) // Insert an element into the set
uniqueNumbers.insert(2)
uniqueNumbers.insert(1) // This is ignored as the set only contains unique elements
```

### **3\. Dictionaries**

Dictionaries store unordered key-value pairs, where the keys are unique:

```swift
var ages = ["John": 30, "Emma": 25] // A dictionary with names as keys and ages as values
print(ages["John"]) // Access the value associated with the key "John"
ages["Mike"] = 40 // Add a new key-value pair
```

### **4\. Stacks**

A stack is a LIFO (Last-In-First-Out) data structure. You can implement a stack in Swift using an Array:

```swift
struct Stack<Element> {
    private var storage: [Element] = [] // An array to store the elements
    
    mutating func push(_ element: Element) {
        storage.append(element) // Adds an element to the top of the stack
    }
    
    mutating func pop() -> Element? {
        return storage.popLast() // Removes and returns the top element
    }
    
    func peek() -> Element? {
        return storage.last // Returns the top element without removing it
    }
}
```

### **5\. Queues**

A queue is a FIFO (First-In-First-Out) data structure. It can be implemented using an array:

```swift
struct Queue<Element> {
    private var storage: [Element] = [] // An array to store the elements
    
    mutating func enqueue(_ element: Element) {
        storage.append(element) // Adds an element to the end of the queue
    }
    
    mutating func dequeue() -> Element? {
        return storage.isEmpty ? nil : storage.removeFirst() // Removes and returns the first element
    }
    
    func peek() -> Element? {
        return storage.first // Returns the first element without removing it
    }
}
```

## **Intermediate Data Structures in Swift**

### **1\. Linked Lists**

A linked list is a linear data structure where each element is a separate object. Each element, or node, contains a reference to the next node in the list. Here's how you can implement a singly linked list in Swift:

```swift
class Node<T> {
    var value: T
    var next: Node?

    init(value: T) {
        self.value = value  // assign the value to the node
    }
}

class LinkedList<T> {
    var head: Node<T>?

    func append(value: T) {
        let newNode = Node(value: value) // create a new node with the value
        if var currentNode = head {
            // if list is not empty, iterate to the end of the list
            while currentNode.next != nil {
                currentNode = currentNode.next!
            }
            currentNode.next = newNode // append the new node at the end of the list
        } else {
            head = newNode // if the list is empty, assign the new node as head
        }
    }
}
```

### **2\. Trees**

Trees are a hierarchical data structure with a set of connected nodes, with one node being designated as the root. The most common type of tree is a binary tree, where each node has up to two children:

```swift
class TreeNode<T> {
    var value: T
    var children: [TreeNode] = []

    init(_ value: T) {
        self.value = value  // assign the value to the node
    }

    func add(_ child: TreeNode) {
        children.append(child)  // add a child node to the current node
    }
}
```

## **Intermediate Algorithms in Swift**

### **1\. Depth-First Search (DFS)**

DFS is a tree or graph traversal algorithm that explores as far as possible along each branch before backtracking. Here's a basic implementation for a tree in Swift:

```swift
extension TreeNode {
    func depthFirstTraversal(visit: (TreeNode) -> Void) {
        visit(self) // Visit the current node
        children.forEach {
            $0.depthFirstTraversal(visit: visit)  // Recursively visit each child
        }
    }
}
```

### **2\. Breadth-First Search (BFS)**

BFS is another traversal algorithm that visits all the nodes of a level before going to the next level. Here's how you can implement it:

```swift
extension TreeNode {
    func breadthFirstTraversal(visit: (TreeNode) -> Void) {
        visit(self)  // Visit the current node
        var queue = [TreeNode]()  // Create a queue
        children.forEach { queue.append($0) }  // Enqueue all the children
        while !queue.isEmpty {
            let node = queue.removeFirst()  // Dequeue a node
            visit(node)  // Visit the dequeued node
            node.children.forEach { queue.append($0) }  // Enqueue all its children
        }
    }
}
```

### **3\. Binary Search Tree (BST)**

A BST is a tree where each node has up to two children. For each node, all elements in the left subtree are less than the node, and all elements in the right subtree are greater. Here's a basic implementation:

```swift
class BinaryNode<T> {
    var value: T
    var leftChild: BinaryNode?
    var rightChild: BinaryNode?

    init(value: T) {
        self.value = value  // assign the value to the node
    }
}

class BinarySearchTree<T: Comparable> {
    private(set) var root: BinaryNode<T>?

    func insert(_ value: T) {
        root = insert(from: root, value: value)  // insert a value into the tree
    }

    private func insert(from node: BinaryNode<T>?, value: T) -> BinaryNode<T> {
        guard let node = node else { return BinaryNode(value: value) }  // if the node is null, create a new node

        // if the value is less than the node's value, insert it into the left subtree
        if value < node.value {
            node.leftChild = insert(from: node.leftChild, value: value)
        } else {
            // if the value is greater than or equal to the node's value, insert it into the right subtree
            node.rightChild = insert(from: node.rightChild, value: value)
        }

        return node  // return the node pointer
    }
}
```

### **Advanced Data Structures in Swift**

### **1\. Graphs**

A graph is a set of nodes where each node can be connected to many other nodes. You can represent graphs in Swift using adjacency lists:

```swift
class Node<T: Hashable>: Hashable {
    let value: T
    var neighbors: [Node]
    
    init(_ value: T) {
        self.value = value
        self.neighbors = []
    }
    
    func hash(into hasher: inout Hasher) {
        hasher.combine(value)
    }
    
    static func == (lhs: Node<T>, rhs: Node<T>) -> Bool {
        return lhs.value == rhs.value
    }
}
    
class Graph<T: Hashable> {
    private var nodes: [Node<T>]
    
    init() {
        self.nodes = []
    }
    
    func createNode(value: T) -> Node<T> {
        let node = Node(value)
        nodes.append(node)
        return node
    }
    
    func addEdge(from: Node<T>, to: Node<T>) {
        from.neighbors.append(to)
    }
}
```

In the code above, we have a `Node` class that holds a value and a list of its neighbors. The `Graph` class holds all the nodes. The `createNode(value:)` method creates a node and adds it to the list of nodes. The `addEdge(from:to:)` method adds an edge between two nodes by appending one node to the neighbor list of the other.

## **Advanced Algorithms in Swift**

### **1\. Dijkstra's Algorithm**

Dijkstra's Algorithm finds the shortest path between nodes in a graph. Here's a simple implementation:

```swift
extension Graph {
    func dijkstraShortestPath(from start: Node<T>, to end: Node<T>) -> [T] {
        var distances: [Node<T>: Double] = [start: 0]
        var previousNodes: [Node<T>: Node<T>] = [:]
        var unvisitedNodes: Set<Node<T>> = Set(nodes)
        
        while let currentNode = unvisitedNodes.min(by: { distances[$0, default: .infinity] < distances[$1, default: .infinity] }) {
            unvisitedNodes.remove(currentNode)
            
            for neighbor in currentNode.neighbors {
                let distanceToNeighbor = distances[currentNode, default: .infinity] + 1  // here we consider the edge weight as 1
                
                if distanceToNeighbor < distances[neighbor, default: .infinity] {
                    distances[neighbor] = distanceToNeighbor
                    previousNodes[neighbor] = currentNode
                    
                    if neighbor == end {
                        var path = [end.value]
                        var currentNode = end
                        
                        while let previousNode = previousNodes[currentNode] {
                            path.append(previousNode.value)
                            currentNode = previousNode
                        }
                        
                        return path.reversed()
                    }
                }
            }
        }
        
        return []
    }
}
```

Dijkstra's algorithm keeps track of the shortest distance to each node in a `distances` dictionary, and also the previous node on the shortest path in a `previousNodes` dictionary. It starts with the start node and visits all the neighbors of the current node, updating the shortest distance to each neighbor and the previous node on the path. When it visits the end node, it constructs the shortest path by tracing back the previous nodes from the end node to the start node.

These are some advanced data structures and algorithms in Swift. Studying these and similar structures and algorithms will give you a deep understanding of computer science and will make you an efficient Swift developer. Remember, practice is key to mastering these concepts!