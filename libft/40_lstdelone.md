### Function Manual: 

ft_lstdelone

#### Overview
The ft_lstdelone function deletes a single element from a linked list, using a specified function to free the content of the element.

#### Function Prototype
```c
void ft_lstdelone(t_list *lst, void (*del)(void *));
```

#### Parameters
- lst: The element to be deleted.
- del: A function pointer to a function used to delete the content of the element.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if the element lst is `NULL`. If it is, the function returns immediately.
2. **Delete Content**: Uses the function del to delete the content of the element.
3. **Free Element**: Frees the memory allocated for the element itself.

#### Code
```c
#include "libft.h"

void	ft_lstdelone(t_list *lst, void (*del)(void *))
{
    if (!lst)
        return ;
    del(lst->content);
    free(lst);
}
```

#### Usage Example
Here is an example of how to use the ft_lstdelone function:
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

    ft_lstdelone(node2, del);

    t_list *current = node1;
    while (current)
    {
        printf("current->content = %s\n", (char *)current->content);
        current = current->next;
    }
    return 0;
}
```

### Visual Explanation
1. **Initial Setup**:
   - List: `node1` -> "Hello, World!"
   - New Element: `node2` -> "Goodbye, World!"
   - New Element: `node3` -> "Hello, Again, World!"
   ```plaintext
   node1 -> "Hello, World!" -> node2 -> "Goodbye, World!" -> node3 -> "Hello, Again, World!" -> NULL
   ```
2. **Function Call**: ft_lstdelone(node2, del)
3. **Step-by-Step Execution**:
   - **Step 1**: Check if lst is `NULL`.
     - lst is `node2`, which is not `NULL`, so continue.
   - **Step 2**: Use del to delete the content of `node2`.
     ```plaintext
     del(node2->content) // Frees "Goodbye, World!"
     ```
   - **Step 3**: Free the memory allocated for `node2`.
     ```plaintext
     free(node2)
     ```
4. **Final List**:
   - `node1` -> "Hello, World!" -> `node3` -> "Hello, Again, World!" -> NULL

### Situations Where ft_lstdelone is Useful
- **Memory Management**: Deleting a specific element from a linked list and freeing its memory.
- **Data Structures**: Managing dynamic data structures that require deletion of individual elements.
- **Garbage Collection**: Implementing custom garbage collection mechanisms where specific elements need to be deleted.
- **Resource Cleanup**: Cleaning up resources associated with a specific element in a linked list.