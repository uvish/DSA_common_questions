**Reversing a link list**
```java
    public ListNode reverseList(ListNode head) {
        ListNode perv=null,next=null,curr=head;
            while(curr!=null)
            {
                next=curr.next;
                curr.next=perv;
                perv=curr;
                curr=next;
            }
            head=perv;
            return head;
    }
```

**Rotate linked List  {1,2,3,4,5} -> rotate by 2 -> {4,5,1,2,3}**
```java
void rotate(int k)
    {
        if (k == 0)
            return;
 
        _Let us understand the below code for example k = 4_
        _and list = 10->20->30->40->50->60_
        Node current = head;
 
        // current will either point to kth or NULL after this
        // loop. current will point to node 40 in the above example
        int count = 1;
        while (count < k && current != null) {
            current = current.next;
            count++;
        }
 
        // If current is NULL, k is greater than or equal to count
        // of nodes in linked list. Don't change the list in this case
        if (current == null)
            return;
 
        // current points to kth node. Store it in a variable.
        // kthNode points to node 40 in the above example
        Node kthNode = current;
 
        // current will point to last node after this loop
        // current will point to node 60 in the above example
        while (current.next != null)
            current = current.next;
 
        // Change next of last node to previous head
        // Next of 60 is now changed to node 10
 
        current.next = head;
 
        // Change head to (k+1)th node
        // head is now changed to node 50
        head = kthNode.next;
 
        // change next of kth node to null
        kthNode.next = null;
    }
```

**Reverse Linked List in Given Size**
```java
 Node reverse(Node head, int k)
    {
        if(head == null)
          return null;
        Node current = head;
        Node next = null;
        Node prev = null;
 
        int count = 0;
 
        /* Reverse first k nodes of linked list */
        while (count < k && current != null) {
            next = current.next;
            current.next = prev;
            prev = current;
            current = next;
            count++;
        }
 
        /* next is now a pointer to (k+1)th node
           Recursively call for the list starting from
           current. And make rest of the list as next of
           first node */
        if (next != null)
            head.next = reverse(next, k);
 
        // prev is now head of input list
        return prev;
    }
```
