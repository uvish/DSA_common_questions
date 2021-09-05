**Left View of Binary Tree**
```java
class Node
{
    int key;
    Node left = null, right = null;
 
    Node(int key) {
        this.key = key;
    }
}
```
```java
    public static void leftView(Node root)
    {
        // return if the tree is empty
        if (root == null) {
            return;
        }
 
        // create an empty queue and enqueue the root node
        Queue<Node> queue = new ArrayDeque<>();
        queue.add(root);
 
        // to store the current node
        Node curr;
 
        // loop till queue is empty
        while (!queue.isEmpty())
        {
            // calculate the total number of nodes at the current level
            int size = queue.size();
            int i = 0;
 
            // process every node of the current level and enqueue their
            // non-empty left and right child
            while (i++ < size)
            {
                curr = queue.poll();
 
                // if this is the first node of the current level, print it
                if (i == 1) {
                    System.out.print(curr.key + " ");
                }
 
                if (curr.left != null) {
                    queue.add(curr.left);
                }
 
                if (curr.right != null) {
                    queue.add(curr.right);
                }
            }
        }
    }
```

**Check if a tree is BST**
```java
boolean isBST()  {
        return isBSTUtil(root, Integer.MIN_VALUE,
                               Integer.MAX_VALUE);
    }
 
    /* Returns true if the given tree is a BST and its
      values are >= min and <= max. */
    boolean isBSTUtil(Node node, int min, int max)
    {
        /* an empty tree is BST */
        if (node == null)
            return true;
 
        /* false if this node violates the min/max constraints */
        if (node.data < min || node.data > max)
            return false;
 
        /* otherwise check the subtrees recursively
        tightening the min/max constraints */
        // Allow only distinct values
        return (isBSTUtil(node.left, min, node.data-1) &&
                isBSTUtil(node.right, node.data+1, max));
    }
 
```

**Inorder Successor of BST**
```java
 Node inOrderSuccessor(Node root, Node n)
    {
 
        // step 1 of the above algorithm
        if (n.right != null) {
            return minValue(n.right);
        }
 
        // step 2 of the above algorithm
        Node p = n.parent;
        while (p != null && n == p.right) {
            n = p;
            p = p.parent;
        }
        return p;
    }
 
    /* Given a non-empty binary search
       tree, return the minimum data 
       value found in that tree. Note that
       the entire tree does not need
       to be searched. */
    Node minValue(Node node)
    {
        Node current = node;
 
        /* loop down to find the leftmost leaf */
        while (current.left != null) {
            current = current.left;
        }
        return current;
    }
    ```