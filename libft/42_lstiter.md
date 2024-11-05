### Function Manual: 

ft_lstiter

#### Overview
The ft_lstiter function iterates over each element of a linked list and applies a given function to the content of each element.

#### Function Prototype
```c
void ft_lstiter(t_list *lst, void (*f)(void *));
```

#### Parameters
- lst: A pointer to the first element of the list.
- f: A function pointer to a function that takes a void pointer as an argument and returns nothing. This function is applied to the content of each element.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if the list pointer lst or the function pointer f is `NULL`. If either is `NULL`, the function returns immediately.
2. **Iterate List**: Iterates through the list, applying the function f to the content of each element.
3. **Move to Next Element**: Moves to the next element in the list and repeats the process until the end of the list is reached.

#### Code
```c
#include "libft.h"

void	ft_lstiter(t_list *lst, void (*f)(void *))
{
    if (!lst || !f)
        return ;
    while (lst)
    {
        f(lst->content);
        lst = lst->next;
    }
}
```

#### Usage Example
Here is an example of how to use the ft_lstiter function:
```c
#include <stdio.h>
#include "libft.h"

void	print_content(void *content)
{
    printf("content = %s\n", (char *)content);
}

int main(void)
{
    t_list *node1 = ft_lstnew("Hello, World!");
    t_list *node2 = ft_lstnew("Goodbye, World!");
    t_list *node3 = ft_lstnew("Hello, Again, World!");

    ft_lstadd_front(&node1, node2);
    ft_lstadd_front(&node1, node3);

    ft_lstiter(node1, print_content);

    return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - List: `node1` -> "Hello, World!"
   - New Element: `node2` -> "Goodbye, World!"
   - New Element: `node3` -> "Hello, Again, World!"
   ```plaintext
   node1 -> "Hello, Again, World!" -> node2 -> "Goodbye, World!" -> node3 -> "Hello, World!" -> NULL
   ```
2. **Function Call**: ft_lstiter(node1, print_content)
3. **Step-by-Step Execution**:
   - **Step 1**: Check if lst or f is `NULL`. Both are not `NULL`, so continue.
   - **Step 2**: Apply f to lst->content:
     - f(node1->content) prints "content = Hello, Again, World!"
   - **Step 3**: Move to the next element:
     - lst = node2
   - **Step 4**: Apply f to lst->content:
     - f(node2->content) prints "content = Goodbye, World!"
   - **Step 5**: Move to the next element:
     - lst = node3
   - **Step 6**: Apply f to lst->content:
     - f(node3->content) prints "content = Hello, World!"
   - **Step 7**: Move to the next element:
     - lst = NULL
   - **Step 8**: End of list, exit the loop.

#### Situations Where ft_lstiter is Useful
- **List Traversal**: Applying a function to each element of a linked list, such as printing or modifying the content.
- **Data Processing**: Processing data stored in a linked list by applying a function to each element.
- **Custom Operations**: Performing custom operations on each element of a list, such as freeing memory or updating values.
- **Debugging**: Printing the content of each element in a list for debugging purposes.