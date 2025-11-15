## Ex21 — Count Number of Nodes in the Left Subtree of a Binary Tree

## AIM:
To design and implement a Java program that constructs a binary tree from given level-order input and counts the number of nodes in the left subtree of the root.

## Algorithm

Read the level-order input into an array.

Construct the binary tree using index relations:

Left child = 2*i + 1

Right child = 2*i + 2

Traverse only the left subtree using recursion.

Count and return the number of nodes.

Display the result.

## Program
```
Program to construct a binary tree from level order input and count nodes
in the left subtree of the root.
Developed by: Naresh P.S.
RegisterNumber: 212223040127
Date: 15-11-2025


class Node {
    int data;
    Node left, right;

    Node(int data) {
        this.data = data;
    }
}

public class LeftSubtreeCount {

    static Node buildTree(int arr[], int i) {
        if (i >= arr.length) return null;

        Node root = new Node(arr[i]);
        root.left = buildTree(arr, 2 * i + 1);
        root.right = buildTree(arr, 2 * i + 2);
        return root;
    }

    static int countNodes(Node root) {
        if (root == null) return 0;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    public static void main(String[] args) {
        int arr[] = {10, 20, 30, 40, 50, 60};

        Node root = buildTree(arr, 0);

        int count = countNodes(root.left);

        System.out.println("Number of nodes in the left subtree: " + count);
    }
}
```

## Output
Number of nodes in the left subtree: 3

## Result

The program constructs the binary tree and correctly counts the number of nodes in the left subtree of the root.
