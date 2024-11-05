### Function Manual: 

ft_lstadd_back

#### Overview
The ft_lstadd_back function adds a new element at the end of a linked list.

#### Function Prototype
```c
void ft_lstadd_back(t_list **lst, t_list *new);
```

#### Parameters
- lst: A pointer to the first element of the list.
- new: The new element to be added to the list.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if both lst and new are not `NULL`. If either is `NULL`, the function does nothing.
2. **Empty List Check**: Checks if the list is empty (i.e., `*lst` is `NULL`). If the list is empty, it sets `*lst` to new.
3. **Find Last Element**: If the list is not empty, it finds the last element of the list using the ft_lstlast function.
4. **Link New Element**: Sets the `next` pointer of the last element to the new element.

#### Code
```c
#include "libft.h"

void	ft_lstadd_back(t_list **lst, t_list *new)
{
    t_list	*last;

    if (!lst || !new)
        return ;
    if (!*lst)
    {
        *lst = new;
        return ;
    }
    last = ft_lstlast(*lst);
    last->next = new;
}
```

#### Usage Example
Here is an example of how to use the ft_lstadd_back function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    t_list *node1 = ft_lstnew("Hello, World!");
    t_list *node2 = ft_lstnew("Goodbye, World!");
    t_list *node3 = ft_lstnew("Hello, Again, World!");

    ft_lstadd_back(&node1, node2);
    ft_lstadd_back(&node1, node3);

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

2. **Function Call**: ft_lstadd_back(&node1, node2)
   - **Step 1**: Check if lst and new are not `NULL`. Both are not `NULL`, so continue.
   - **Step 2**: Check if the list is empty (`*lst` is `NULL`). It is not empty, so continue.
   - **Step 3**: Find the last element of the list using ft_lstlast.
     - Last element is `node1`.
   - **Step 4**: Set `node1->next` to `node2`.

3. **Function Call**: ft_lstadd_back(&node1, node3)
   - **Step 1**: Check if lst and new are not `NULL`. Both are not `NULL`, so continue.
   - **Step 2**: Check if the list is empty (`*lst` is `NULL`). It is not empty, so continue.
   - **Step 3**: Find the last element of the list using ft_lstlast.
     - Last element is `node2`.
   - **Step 4**: Set `node2->next` to `node3`.

4. **Final List**:
   - `node1` -> "Hello, World!" -> `node2` -> "Goodbye, World!" -> `node3` -> "Hello, Again, World!"

#### Situations Where ft_lstadd_back is Useful
- **Appending Elements**: Adding elements to the end of a linked list.
- **Queue Implementation**: Implementing a queue where elements are added to the back.
- **Dynamic Data Structures**: Managing dynamic data structures that require frequent insertion at the end.
- **Data Processing**: Appending elements to a list for processing in the order they were added.