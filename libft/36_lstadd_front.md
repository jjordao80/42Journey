### Function Manual: 

ft_lstadd_front

#### Overview
The ft_lstadd_front function adds a new element at the beginning of a linked list.

#### Function Prototype
```c
void ft_lstadd_front(t_list **lst, t_list *new);
```

#### Parameters
- lst: A pointer to the first element of the list.
- new: The new element to be added to the list.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if both lst and new are not `NULL`. If either is `NULL`, the function does nothing.
2. **Link New Element**: Sets the `next` pointer of the new element to the current first element of the list.
3. **Update List Head**: Updates the head of the list to point to the new element.

#### Code
```c
#include "libft.h"

void	ft_lstadd_front(t_list **lst, t_list *new)
{
    if (lst && new)
    {
        new->next = *lst;
        *lst = new;
    }
}
```

#### Usage Example
Here is an example of how to use the ft_lstadd_front function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    t_list *node1 = ft_lstnew("Hello, World!");
    t_list *node2 = ft_lstnew("Goodbye, World!");
    t_list *node3 = ft_lstnew("Hello, Again, World!");

    ft_lstadd_front(&node1, node2);
    ft_lstadd_front(&node1, node3);

    t_list *current = node1;
    while (current)
    {
        printf("current->content = %s\n", (char *)current->content);
        current = current->next;
    }

    return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - List: `node1` -> "Hello, World!"
   - New Element: `node2` -> "Goodbye, World!"
   - New Element: `node3` -> "Hello, Again, World!"

2. **Function Call**: 

ft_lstadd_front(&node1, node2)


   - **Step 1**: Check if lst and new are not `NULL`. Both are not `NULL`, so continue.
   - **Step 2**: Set new->next to `*lst` (i.e., `node2->next` to `node1`).
   - **Step 3**: Update `*lst` to new (i.e., `node1` to `node2`).

3. **Function Call**: 

ft_lstadd_front(&node1, node3)
   - **Step 1**: Check if lst and new are not `NULL`. Both are not `NULL`, so continue.
   - **Step 2**: Set new->next to `*lst` (i.e., `node3->next` to `node2`).
   - **Step 3**: Update `*lst` to new (i.e., `node1` to `node3`).

4. **Final List**:
   - `node1` -> "Hello, Again, World!"
   - `node3->next` -> "Goodbye, World!"
   - `node2->next` -> "Hello, World!"

### Additional Examples

#### Example 1: Adding Multiple Nodes to the Front
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    t_list *node1 = ft_lstnew("First Node");
    t_list *node2 = ft_lstnew("Second Node");
    t_list *node3 = ft_lstnew("Third Node");

    ft_lstadd_front(&node1, node2);
    ft_lstadd_front(&node1, node3);

    t_list *current = node1;
    while (current)
    {
        printf("current->content = %s\n", (char *)current->content);
        current = current->next;
    }

    return 0;
}
```
**Explanation**:
- This example creates three nodes and adds them to the front of the list one by one.
- The final list order will be: "Third Node" -> "Second Node" -> "First Node".

#### Example 2: Using 

ft_lstadd_front in a Function to Build a List
```c
#include <stdio.h>
#include "libft.h"

void add_to_front(t_list **head, char *content)
{
    t_list *new_node = ft_lstnew(content);
    ft_lstadd_front(head, new_node);
}

int main(void)
{
    t_list *head = NULL;

    add_to_front(&head, "Node 1");
    add_to_front(&head, "Node 2");
    add_to_front(&head, "Node 3");

    t_list *current = head;
    while (current)
    {
        printf("current->content = %s\n", (char *)current->content);
        current = current->next;
    }

    return 0;
}
```
**Explanation**:
- This example defines a function `add_to_front` that adds a new node to the front of the list.
- It then creates a list with three nodes by calling `add_to_front` multiple times.
- The final list order will be: "Node 3" -> "Node 2" -> "Node 1".

#### Example 3: Prepending Elements to a List for Reverse Processing
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    t_list *head = NULL;

    char *words[] = {"one", "two", "three", "four"};
    for (int i = 0; i < 4; i++)
    {
        t_list *new_node = ft_lstnew(words[i]);
        ft_lstadd_front(&head, new_node);
    }

    t_list *current = head;
    while (current)
    {
        printf("current->content = %s\n", (char *)current->content);
        current = current->next;
    }

    return 0;
}
```
**Explanation**:
- This example creates a list by prepending elements from an array of strings.
- The final list order will be: "four" -> "three" -> "two" -> "one".
- This approach is useful for processing elements in reverse order of their addition.

#### Situations Where ft_lstadd_front is Useful
- **Creating Linked Lists**: Adding elements to the beginning of a linked list.
- **Stack Implementation**: Implementing a stack where elements are added to the top.
- **Dynamic Data Structures**: Managing dynamic data structures that require frequent insertion at the beginning.
- **Data Processing**: Prepending elements to a list for processing in reverse order.

### Difference Between `ft_lstnew` and `ft_lstadd_front`

#### `ft_lstnew`
- **Purpose**: Creates a new list element.
- **Function Prototype**:
  ```c
  t_list *ft_lstnew(void *content);
  ```
- **Parameters**:
  - `content`: The content to store in the new element.
- **Return Value**: A pointer to the new element.
- **Usage**: Used to create a new node with the given content.
- **Example**:
  ```c
  t_list *node = ft_lstnew("Hello, World!");
  ```

#### `ft_lstadd_front`
- **Purpose**: Adds a new element at the beginning of a linked list.
- **Function Prototype**:
  ```c
  void ft_lstadd_front(t_list **lst, t_list *new);
  ```
- **Parameters**:
  - `lst`: A pointer to the first element of the list.
  - `new`: The new element to be added to the list.
- **Return Value**: None.
- **Usage**: Used to prepend a new node to the beginning of an existing list.
- **Example**:
  ```c
  t_list *node1 = ft_lstnew("Hello, World!");
  t_list *node2 = ft_lstnew("Goodbye, World!");
  ft_lstadd_front(&node1, node2);
  ```

### Summary
- `ft_lstnew` is used to create a new list element.
- `ft_lstadd_front` is used to add an existing element to the front of a list.