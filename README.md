# JavaAndCProfiling [Open this file in raw mode for better visiblity]
Profiling assignment for Java and C for new engineers.

Please watch your Home Work Kapsules here:- http://kpoint.gslab.com/playlist/view/128

Submission of Assignment:-

1) After completion of assignment send corrected file to email: gaurav.dhadiwal@gslab.com,mahendra.patel@gslab.com

2) Only share the required files example only modified bst.c for Q1.
3) Please mention new complexity of Q2 in email.   

First Assignment:- C
Q1. C Debugging Assignment.  ( Code is present in eclipse on given VM at /gslab/workspace/C_debugging_assignment. Check the file bst.c )
	Below is Implementation for Binary search tree (present in file  bst.c eclipse project:C-debugging_assignment).  Unfortunately this code crashes(gives segmentation fault) at many places. find all such places and correct the code.


Note: 1) Your aim is to correct below code not to write new code, so just correct the error rather than replace the algorithm.
2)  Code is written in such fashion so it is easy to understand. Still if you want to know more about code algorithm and logic of binary search tree please refer appendix A below.

Second Assignemnt:- Java

Q2. Java Profiling & Debugging (The code is already added in eclipes)

Problem Statement: 
Find out the missing number from given set of numbers.  The size of the input can be anything. Numbers are in increasing order i.e a<b<c…..<n and difference between any two consecutive numbers is atmost 2.  

Ex: Input    : {2,3,4,6,7} 
      Output : 5

Implementation Details : 
This program reads the numbers from file (number are stored in comma (,) separated format)  and then prints out the missing number.  

Bug: This program has a bug. It won’t give desired output when input numbers are > 9. 

Assignment:- 
	1. fix the bug
	2. Find out the time complexity of the current program.
	3. profile the program  to improve the time complexity
	4. find out the time complexity of improved version.


							Appendix  A

Insertion, Deletion And Traversal In Binary Search Tree
Insertion in Binary Search Tree:
Check whether root node is present or not(tree available or not).  If root is NULL, create root node.
If the element to be inserted is less than the element present in the root node, traverse the left sub-tree recursively until we reach T->left/T->right is NULL and place the new node at T->left(key in new node < key in T)/T->right (key in new node > key in T).
If the element to be inserted is greater than the element present in root node, traverse the right sub-tree recursively until we reach T->left/T->right is NULL and place the new node at T->left/T->right.

Algorithm for insertion in Binary Search Tree:
TreeNode insert(int data, TreeNode T) {
          if T is NULL {
                  T = (TreeNode *)malloc(sizeof (Struct TreeNode));
                  (Allocate Memory of new node and load the data into it)
                  T->data = data;
                  T->left   = NULL;
                  T->right = NULL;
          } else if T is less than T->left {
                  T->left = insert(data, T->left);
                  (Then node needs to be inserted in left sub-tree.So, 
                    recursively traverse left sub-tree to find the place 
                    where the new node needs to be inserted)
          } else if T is greater than T->right {
                   T->right = insert(data, T->right);
                   (Then node needs to be inserted in right sub-tree
                    So, recursively traverse right sub-tree to find the 
                     place where the new node needs to be inserted.)
         }
         return T;
}

Example:
Insert 20 into the Binary Search Tree.  
Tree is not available.  So, create root node and place 10 into it.

                                                   20

Insert 23 into the given Binary Search Tree. 23 > 20 (data in root).  So, 23 needs to be inserted in the right sub-tree of 20.

                                                    20
                                                        \
                                                         23

Insert 13 into the given Binary Search Tree.  13 < 20(data in root).  So, 13 needs to be inserted in left sub-tree of 20.

                                                   20
                                                 /     \
                                              13       23

Insert 9 into the given Binary Search Tree.

                                                   20
                                                 /     \
                                              13       23
                                             /
                                           9 

Inserting 14.

                                                   20
                                                 /     \
                                              13       23
                                             /    \   
                                           9      14

Inserting 19.
                                                   20
                                                 /     \
                                              13       23
                                             /    \   
                                           9      14
                                                     \
                                                      19
Inserting 21.

                                                    20
                                                 /      \
                                              13        23
                                             /    \      / 
                                           9      14  21  
                                                     \
                                                      19
Inserting 27.
                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14  21  27
                                                     \
                                                      19
Inserting 24.
                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14  21  27
                                                     \       /
                                                      19  24


Deletion in Binary Search Tree:
How to delete a node from binary search tree?
There are three different cases that needs to be considered for deleting a node from binary search tree.

case 1: Node with no children (or) leaf node
case 2: Node with one child
case 3: Node with two children.

                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14  21  27
                                                     \       /
                                                      19  24

Case 1: Delete a leaf node/ node with no children.

                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14  21  27
                                                     \       /
                                                      19  24

Delete 24 from the above binary search tree.

                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14    21  27
                                                     \      
                                                      19

Case 2: Delete a node with one child.

                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14    21  27
                                                     \       /
                                                      19  24

Delete 14 from above binary search tree.

                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      19    21  27
                                                             /
                                                           24

Case 3: Delete a node with two children.
Delete a node whose right child is the smallest node in the right sub-tree. (14 is the smallest node present in the right sub-tree of 13).
                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14    21  27
                                                     \       /
                                                      19  24

Delete 13 from the above binary tree.  Find the smallest in the left subtree of 13.  So, replace 13 with 14.

                                                    20
                                                 /      \
                                              14        23
                                             /   \       /  \
                                           9      19  21  27
                                                             /
                                                          24

Delete 20 from the below binary search tree.
                                                    20
                                                 /      \
                                              13        23
                                             /    \      /  \
                                           9      14    21  27
                                                          \
                                                          22

Find the smallest node in the right sub-tree of 20.  And that smallest node is 21.  So, replace 20 with 21.  Since 21 has only one child(22), the pointer currently pointing to 21 is made to point to 22.  So, the resultant binary tree would be the below.

                                                    21
                                                 /      \
                                              13        23
                                             /    \     /  \
                                           9      14    Del  27
                                                          \
                                                          22

                                                    21
                                                 /      \
                                              13        23
                                             /    \     /   \
                                           9      14  22   27
                                                         
Sample Run of code:
  Output: (C Program For Insertion, Deletion & Traversal In BST Tree)
  jp@jp-VirtualBox:$ ./a.out
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:1
  Enter your data:20
  Continue Insertion(0/1):1
  Enter your data:14
  Continue Insertion(0/1):1
  Enter your data:9
  Continue Insertion(0/1):1
  Enter your data:19
  Continue Insertion(0/1):1
  Enter your data:25
  Continue Insertion(0/1):1
  Enter your data:21
  Continue Insertion(0/1):1
  Enter your data:23
  Continue Insertion(0/1):1
  Enter your data:30
  Continue Insertion(0/1):1
  Enter your data:26
  Continue Insertion(0/1):0    
  Resultant Binary Search Tree after insertion operation:
                                                    20
                                                 /      \
                                              14          25
                                             /    \      /   \
                                            9      19  21      30
                                                         \      /
                                                        23   26 
    
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:4
  Inorder Traversal:
  9 14 19 20 21 23 25 26 30
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:2
  Enter your data:9

  Delete node 9
                                                    20
                                                 /      \
                                                14        25
                                                  \      /   \
                                                    19  21   30
                                                         \      /
                                                          23   26

  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:4
  Inorder Traversal:
  14 19 20 21 23 25 26 30
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:2
  Enter your data:14

  Delete node 14
                                                    20
                                                 /      \
                                              19        25
                                                         /   \
                                                        21   30
                                                         \      /
                                                        23   26

  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:4
  Inorder Traversal:
  19 20 21 23 25 26 30
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:2
  Enter your data:30

  Delete node 30
                                                    20
                                                 /      \
                                              19        25
                                                         /   \
                                                        21   26
                                                         \      
                                                         23   

  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:4
  Inorder Traversal:
  19 20 21 23 25 26
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:2
  Enter your data:20

  Delete node 20
                                                    21
                                                 /      \
                                              19        25
                                                         /   \
                                                        23   26
                                                             
                                                            

  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:4
  Inorder Traversal:
  19 21 23 25 26
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:1
  Enter your data:15
  Continue Insertion(0/1):1
  Enter your data:14
  Continue Insertion(0/1):1
  Enter your data:16
  Continue Insertion(0/1):1
  Enter your data:17
  Continue Insertion(0/1):0
  Binary Search Tree After Insertion Operation:

                                                    21
                                                 /      \
                                              19        25
                                             /            /   \
                                           15         23   26
                                          /   \
                                        14   16
                                                 \ 
                                                 17 

  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:4
  Inorder Traversal:
  14 15 16 17 19 21 23 25 26
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:2
  Enter your data:15
  Delete Node 15

                                                    21
                                                 /      \
                                              19        25
                                             /            /   \
                                           16         23   26
                                          /   \
                                        14   17

  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:4
  Inorder Traversal:
  14 16 17 19 21 23 25 26
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:3
  Enter value for data:21
  data found: 21
  1. Insertion in Binary Search Tree
  2. Deletion in Binary Search Tree
  3. Search Element in Binary Search Tree
  4. Inorder traversal
  5. Exit
  Enter your choice:5
