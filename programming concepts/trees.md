# Trees
Trees are a prevalent data structure, and are important to understand. They consist of nodes with a datum value, and at the most basic, a left and right node, which are often seen as child nodes. Every node can also have a relation with their parent node, with the exception of the root which has no parent node. Because of a tree's feature, they are able to hold massive amounts of data without having a lot of height.

### **Terminology**
**Root Node** first node without parents
**Leaf Nodes** are end/bottom nodes with no children
**Size** is the total # of elements
**Height** is the longest chain of nodes from root to leaf

<u>**Different Types of Trees**</u>  
**Tree:** regular tree that consists of nodes that are connected without any cycles. Also, two nodes from any point in the tree will only have one shortest unique path.  
**Directed Tree:** a tree that exhibits child parent relationships (you can call node->parent)      
**Binary Tree/BST:** has only either 0, 1, or 2 children per node. if the values have to go in a specific order then it is a BST, else it's just a regular binary tree. 

### **Node Representation**  
```cpp
struct Node {
    Node *parent; // not always necessary if regular tree
    Node *left;
    Node *right;
    int datum; // can be anything (string, char, bool, etc)
}
```

### **Recursive Computations**
There are recursive functions that can find out the size and height of any given tree. Remember that recursive functions only aim to solve the current problem/question, and then calls itself again to solve the next iteration of the question. They are below and commented:

**Size:**
```cpp
// passed in as a pointer, so use -> to refer to its elements.
int size(Node *node) {

    // two cases: if empty, the size is zero
    if (!node) {
        return 0;
    }

    // else: current size is 1 + size of left & right children. 
    else {
        return 1 + size(node->right) + size(node->left);
    }
}
```
**Height:**
```cpp
int height(Node *node) {

    // two cases: if empty, the height is 0
    if (!node) {
        return 0;
    }

    // else: current height is 1 + max of left height and right height
    else {
        return 1 + max(height(node->right), height(node->left));
    }
}
```
> just a note that the right and left children can be called in any order and will still work.

**Tree Printing**: There are many ways to print trees. The three most popular tree traversals are:
- preorder: processing the node **before** going to both recursive calls
```cpp
if (node) {
    cout << node->datum << endl; // processing the node
    print(node->left); // recursive call left
    print(node->right); // recursive call right
}
```
- inorder: process the node in **between** recursive calls
```cpp
if (node) {
    print(node->left); // process the left node
    cout << node->datum << endl; // process node in between calls
    print(node->right); // process right node
}
```
- postorder: process the node **after** recursive calls
```cpp
if (node) {
    print(node->left); // process the left node
    print(node->right); // process right node
    cout << node->datum << endl; // process node in after calls
}
```

### **Special Type of Trees**
There is a special representation of a type of tree, and that is a heap/priority queue. These are usually represented in the form of an array or vector. Some special characteristics is that it must be a **complete binary tree** and have heap ordering (priority).

There are two types of heap/priority trees:
1. Max Priority Queue: prioritizes the largest element in the array as the next element. 
> remember that the comparator to be used to create a max priority queue is `std:less`. more specifically, the inside must be `return left < right;` and return true if the priority is lower. 
2. Min Priority Queue: prioritizes the smallest element in the array as the next element. 
> remember that the comparator to be used to create a min priority queue is `std:greater`. more specifically, the inside must be `return left > right;` and return true if the priority is lower. 

