### Function Manual: 

ft_lstlast

#### Overview
The ft_lstlast function returns the last element of a linked list.

#### Function Prototype
```c
t_list *ft_lstlast(t_list *lst);
```

#### Parameters
- lst: A pointer to the first element of the list.

#### Return Value
- Returns a pointer to the last element of the list.
- Returns `NULL` if the list is empty.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if the input list lst is `NULL`. If it is, returns `NULL`.
2. **Traverse List**: Iterates through the list until it reaches the last element.
3. **Return Last Element**: Returns a pointer to the last element of the list.

#### Code
```c
#include "libft.h"

t_list	*ft_lstlast(t_list *lst)
{
    if (!lst)
        return (NULL);
    while (lst->next)
        lst = lst->next;
    return (lst);
}
```

#### Usage Example
Here is an example of how to use the ft_lstlast function:
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

    t_list *last = ft_lstlast(node1);
    printf("last->content = %s\n", (char *)last->content);

    return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - List: `node1` -> "Hello, World!"
   - New Element: `node2` -> "Goodbye, World!"
   - New Element: `node3` -> "Hello, Again, World!"
2. **Function Call**: ft_lstlast(node1)
3. **Step-by-Step Execution**:
   - **Step 1**: Check if lst is `NULL`. It is not `NULL`, so continue.
   - **Step 2**: Traverse the list:
     - lst is `node1` -> "Hello, World!"
     - Move to the next node: lst is `node2` -> "Goodbye, World!"
     - Move to the next node: lst is `node3` -> "Hello, Again, World!"
     - lst->next is `NULL`, so stop.
   - **Step 3**: Return the last element, which is `node3`.

#### Situations Where ft_lstlast is Useful
- **List Management**: Finding the last element of a linked list for operations like appending new elements.
- **Data Processing**: Accessing the last element of a list for processing or analysis.
- **Dynamic Data Structures**: Managing dynamic data structures that require knowledge of the last element.
- **Traversal**: When you need to traverse a list and perform operations on the last element.