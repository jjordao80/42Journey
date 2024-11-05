### Function Manual: 

ft_lstclear

#### Overview
The ft_lstclear function deletes and frees the memory of all elements in a linked list, using a specified function to free the content of each element.

#### Function Prototype
```c
void ft_lstclear(t_list **lst, void (*del)(void *));
```

#### Parameters
- lst: A pointer to the first element of the list.
- del: A function pointer to a function used to delete the content of each element.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if the list pointer lst or the delete function del is `NULL`. If either is `NULL`, the function returns immediately.
2. **Traverse List**: Iterates through the list, deleting each element.
3. **Delete Element**: Uses the function del to delete the content of each element.
4. **Free Element**: Frees the memory allocated for each element.
5. **Update List Head**: Sets the list head to `NULL` after clearing all elements.

#### Code
```c
#include "libft.h"

void	ft_lstclear(t_list **lst, void (*del)(void *))
{
    t_list	*tmp;

    if (!lst || !del)
        return ;
    while (*lst)
    {
        tmp = (*lst)->next;
        ft_lstdelone(*lst, del);
        *lst = tmp;
    }
}
```

#### Usage Example
Here is an example of how to use the ft_lstclear function:
```c
#include <stdio.h>
#include "libft.h"

void	del(void *content)
{
    free(content);
}

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

    ft_lstclear(&node1, del);

    return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - List: `node1` -> "Hello, World!"
   - New Element: `node2` -> "Goodbye, World!"
   - New Element: `node3` -> "Hello, Again, World!"
   ```plaintext
   node1 -> "Hello, World!" -> node2 -> "Goodbye, World!" -> node3 -> "Hello, Again, World!" -> NULL
   ```

2. **Function Call**: ft_lstclear(&node1, del)
3. **Step-by-Step Execution**:
   - **Step 1**: Check if lst or del is `NULL`. Both are not `NULL`, so continue.
   - **Step 2**: Iterate through the list:
     - **Iteration 1**:
       - `tmp` is set to `node2`.
       - ft_lstdelone(node1, del) is called, freeing "Hello, World!".
       - `node1` is updated to `tmp` (i.e., `node2`).
     - **Iteration 2**:
       - `tmp` is set to `node3`.
       - ft_lstdelone(node2, del) is called, freeing "Goodbye, World!".
       - `node2` is updated to `tmp` (i.e., `node3`).
     - **Iteration 3**:
       - `tmp` is set to `NULL`.
       - ft_lstdelone(node3, del) is called, freeing "Hello, Again, World!".
       - `node3` is updated to `tmp` (i.e., `NULL`).
   - **Step 3**: Set `*lst` to `NULL`.

4. **Final List**:
   - The list is now empty, and `node1` is `NULL`.

#### Situations Where ft_lstclear is Useful
- **Memory Management**: Deleting all elements in a linked list and freeing their memory.
- **Data Structures**: Managing dynamic data structures that require clearing of all elements.
- **Garbage Collection**: Implementing custom garbage collection mechanisms where all elements in a list need to be deleted.
- **Resource Cleanup**: Cleaning up resources associated with all elements in a linked list.