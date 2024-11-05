### Function Manual: `ft_lstnew`

#### Overview
The `ft_lstnew` function creates a new list node with the given content.

#### Function Prototype
```c
t_list *ft_lstnew(void *content);
```

#### Parameters
- `content`: The content to be stored in the new list node.

#### Return Value
- Returns a pointer to the newly created list node.
- Returns `NULL` if the memory allocation fails.

#### Detailed Explanation
The function performs the following steps:
1. **Memory Allocation**: Allocates memory for a new list node.
2. **Null Check**: Checks if the allocation was successful. If not, returns `NULL`.
3. **Initialize Node**: Initializes the node's content with the provided content and sets the next pointer to `NULL`.
4. **Return Node**: Returns the pointer to the newly created node.

#### Code
```c
#include "libft.h"

t_list	*ft_lstnew(void *content)
{
    t_list	*n;

    n = malloc(sizeof(t_list));
    if (!n)
        return (NULL);
    n->content = content;
    n->next = NULL;
    return (n);
}
```

#### Usage Example
Here is an example of how to use the `ft_lstnew` function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    t_list *node1 = ft_lstnew("Node 1");
    t_list *node2 = ft_lstnew("Node 2");
    t_list *node3 = ft_lstnew("Node 3");

    node1->next = node2;
    node2->next = node3;

    t_list *current = node1;
    while (current != NULL)
    {
        printf("node->content = %s\n", (char *)current->content);
        current = current->next;
    }
    return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - Content to store: "Node 1", "Node 2", "Node 3"
2. **Function Call**: `ft_lstnew("Node 1")`, `ft_lstnew("Node 2")`, `ft_lstnew("Node 3")`
3. **Step-by-Step Execution**:
   - **Step 1**: Allocate memory for a new list node.
     - `n = malloc(sizeof(t_list))`
   - **Step 2**: Check if the allocation was successful.
     - If `n` is `NULL`, return `NULL`.
   - **Step 3**: Initialize the node's content and next pointer.
     - `n->content = "Node 1"`
     - `n->next = NULL`
   - **Step 4**: Return the pointer to the new node.
     - Return `n`

#### What is a List Node?
A list node is a fundamental building block of a linked list. It typically contains:
- **Content**: The data stored in the node.
- **Next Pointer**: A pointer to the next node in the list.

#### What is a Linked List?
A linked list is a data structure consisting of a sequence of nodes. Each node contains data and a reference (or link) to the next node in the sequence. Linked lists are used for:
- **Dynamic Memory Allocation**: Efficiently using memory by allocating nodes as needed.
- **Ease of Insertion/Deletion**: Quickly inserting or deleting nodes without reorganizing the entire structure.
- **Implementing Other Data Structures**: Serving as the basis for stacks, queues, and other dynamic data structures.

#### Situations Where `ft_lstnew` is Useful
- **Creating Linked Lists**: Initializing the first node of a linked list.
- **Data Storage**: Storing data in a dynamically allocated list structure.
- **List Manipulation**: Creating new nodes to be added to an existing list.
- **Dynamic Data Structures**: Implementing dynamic data structures that require node creation, such as stacks, queues, or custom linked lists.

### Detailed Examples

#### Example 1: Creating a Single Node
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    t_list *node = ft_lstnew("Hello, World!");
    printf("node->content = %s\n", (char *)node->content);
    return 0;
}
```
**Explanation**:
- This example creates a single node with the content "Hello, World!" and prints the content.

#### Example 2: Creating Multiple Nodes and Linking Them
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    t_list *node1 = ft_lstnew("Node 1");
    t_list *node2 = ft_lstnew("Node 2");
    t_list *node3 = ft_lstnew("Node 3");

    node1->next = node2;
    node2->next = node3;

    t_list *current = node1;
    while (current != NULL)
    {
        printf("node->content = %s\n", (char *)current->content);
        current = current->next;
    }
    return 0;
}
```
**Explanation**:
- This example creates three nodes and links them together to form a simple linked list. It then traverses the list and prints the content of each node.
- `current` is a pointer used to traverse the list. It starts at `node1` and moves to the next node using `current = current->next` until it reaches the end of the list (`current == NULL`).

#### Example 3: Using `ft_lstnew` in a Function to Add Nodes to a List
```c
#include <stdio.h>
#include "libft.h"

void add_node(t_list **head, void *content)
{
    t_list *new_node = ft_lstnew(content);
    new_node->next = *head;
    *head = new_node;
}

int main(void)
{
    t_list *head = NULL;

    add_node(&head, "Node 1");
    add_node(&head, "Node 2");
    add_node(&head, "Node 3");

    t_list *current = head;
    while (current != NULL)
    {
        printf("node->content = %s\n", (char *)current->content);
        current = current->next;
    }
    return 0;
}
```
**Explanation**:
- This example defines a function `add_node` that adds a new node to the beginning of a linked list. It then creates a list with three nodes and prints the content of each node.
- `head` is a pointer to the first node in the list. The `add_node` function updates `head` to point to the new node each time a node is added.
- `current` is used to traverse the list and print the content of each node.
