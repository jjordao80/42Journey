### Function Manual: 

ft_lstmap

#### Overview
The ft_lstmap function iterates over each element of a linked list, applies a given function to the content of each element, and creates a new list with the results. If an allocation fails, it uses a specified function to delete the content of each element in the new list.

#### Function Prototype
```c
t_list *ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *));
```

#### Parameters
- lst: A pointer to the first element of the list.
- f: A function pointer to a function that takes a void pointer as an argument and returns a void pointer. This function is applied to the content of each element.
- del: A function pointer to a function that takes a void pointer as an argument and returns nothing. This function is used to delete the content of each element if an allocation fails.

#### Return Value
- Returns a pointer to the first element of the new list.
- Returns `NULL` if the allocation fails.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if the list pointer lst or the function pointer f is `NULL`. If either is `NULL`, the function returns `NULL`.
2. **Initialize New List**: Initializes a new list pointer new to `NULL`.
3. **Iterate List**: Iterates through the original list lst.
4. **Apply Function**: Applies the function f to the content of each element and creates a new element with the result.
5. **Check Allocation**: Checks if the allocation of the new element was successful. If not, it clears the new list using ft_lstclear and returns `NULL`.
6. **Add to New List**: Adds the new element to the end of the new list using ft_lstadd_back.
7. **Move to Next Element**: Moves to the next element in the original list and repeats the process.
8. **Return New List**: Returns the new list.

#### Code
```c
#include "libft.h"

t_list	*ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *))
{
    t_list	*new;
    t_list	*tmp;

    if (!lst || !f)
        return (NULL);
    new = NULL;
    while (lst)
    {
        tmp = ft_lstnew(f(lst->content));
        if (!tmp)
        {
            ft_lstclear(&new, del);
            return (NULL);
        }
        ft_lstadd_back(&new, tmp);
        lst = lst->next;
    }
    return (new);
}
```

#### Usage Example
Here is an example of how to use the ft_lstmap function:
```c
#include <stdio.h>
#include "libft.h"

void	del(void *content)
{
    free(content);
}

void	*add_one(void *content)
{
    int	*new_content;
    new_content = malloc(sizeof(int));
    if (!new_content)
        return (NULL);
    *new_content = *(int *)content + 1;
    return (new_content);
}

int main(void)
{
    t_list *node1 = ft_lstnew(malloc(sizeof(int)));
    t_list *node2 = ft_lstnew(malloc(sizeof(int)));
    t_list *node3 = ft_lstnew(malloc(sizeof(int)));
    *(int *)node1->content = 1;
    *(int *)node2->content = 2;
    *(int *)node3->content = 3;
    ft_lstadd_front(&node1, node2);
    ft_lstadd_front(&node1, node3);
    t_list *new = ft_lstmap(node1, add_one, del);
    t_list *current = new;
    while (current)
    {
        printf("current->content = %d\n", *(int *)current->content);
        current = current->next;
    }
    ft_lstclear(&node1, del);
    ft_lstclear(&new, del);
    return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - Original List: `node1` -> 1, `node2` -> 2, `node3` -> 3
   - Function f: `add_one` (increments the integer content by 1)
   - Function del: del (frees the content)
2. **Function Call**: ft_lstmap(node1, add_one, del)
3. **Step-by-Step Execution**:
   - **Step 1**: Check if lst or f is `NULL`. Both are not `NULL`, so continue.
   - **Step 2**: Initialize new to `NULL`.
   - **Step 3**: Iterate through the original list:
     - **Iteration 1**:
       - Apply f to `node1->content` (1), result is 2.
       - Create a new element with content 2.
       - Add the new element to new.
       - Move to `node2`.
     - **Iteration 2**:
       - Apply f to `node2->content` (2), result is 3.
       - Create a new element with content 3.
       - Add the new element to new.
       - Move to `node3`.
     - **Iteration 3**:
       - Apply f to `node3->content` (3), result is 4.
       - Create a new element with content 4.
       - Add the new element to new.
       - Move to `NULL`.
   - **Step 4**: Return the new list.

#### Situations Where ft_lstmap is Useful
- **Data Transformation**: Applying a transformation function to each element of a list and creating a new list with the results.
- **Data Processing**: Processing data stored in a linked list by applying a function to each element and storing the results in a new list.
- **Custom Operations**: Performing custom operations on each element of a list and creating a new list with the results.
- **Memory Management**: Managing dynamic data structures that require creating new lists based on existing ones.