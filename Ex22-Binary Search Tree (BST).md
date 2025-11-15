## Ex22 — Searching for a Book ID in a BST

## AIM:
To design and implement a Java program that constructs a Binary Search Tree (BST) using Book IDs and searches for a given Book ID.

## Algorithm

Create a BST by inserting book IDs one by one.

Use recursion to insert nodes based on BST rules.

Accept a Book ID to search for.

Traverse the BST and check if the Book ID exists.

Display appropriate result.

## Program
```
Program to construct a Binary Search Tree (BST) and search for a Book ID.
Developed by: Naresh P.S.
RegisterNumber: 212223040127
Date: 15-11-2025

class BSTNode {
    int data;
    BSTNode left, right;

    BSTNode(int data) {
        this.data = data;
    }
}

public class BookIDSearchBST {

    static BSTNode insert(BSTNode root, int data) {
        if (root == null) return new BSTNode(data);
        if (data < root.data) root.left = insert(root.left, data);
        else root.right = insert(root.right, data);
        return root;
    }

    static boolean search(BSTNode root, int key) {
        if (root == null) return false;
        if (root.data == key) return true;
        return key < root.data ? search(root.left, key) : search(root.right, key);
    }

    public static void main(String[] args) {
        int books[] = {50, 30, 70, 20, 40, 60, 80};
        BSTNode root = null;

        for (int id : books) root = insert(root, id);

        int findID = 40;

        if (search(root, findID))
            System.out.println("Book ID " + findID + " found in the library system.");
        else
            System.out.println("Book ID " + findID + " not found.");
    }
}
```

## Output
Book ID 40 found in the library system.

## Result

The program constructs a BST from book IDs and successfully checks whether a specific book ID exists.
