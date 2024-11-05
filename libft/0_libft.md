### Function Manual: 
`#ifndef` and `#define` Preprocessor Directives

#### Overview
The `#ifndef` and `#define` preprocessor directives are used to prevent multiple inclusions of the same header file, which can cause errors and increase compilation time.

#### Syntax
```c
#ifndef HEADER_NAME_H
#define HEADER_NAME_H

// Header file content

#endif /* HEADER_NAME_H */
```

#### Detailed Explanation
The directives perform the following steps:
1. **Check if Not Defined**: `#ifndef HEADER_NAME_H` checks if `HEADER_NAME_H` is not defined.
2. **Define the Header**: `#define HEADER_NAME_H` defines `HEADER_NAME_H` to prevent future inclusions.
3. **Include Guard**: The content of the header file is included only if `HEADER_NAME_H` was not previously defined.
4. **End of Guard**: `#endif` marks the end of the include guard.

#### Code Example
```c
#ifndef LIBFT_H
#define LIBFT_H

#include <stdlib.h>
#include <unistd.h>

typedef struct s_list
{
    void            *content;
    struct s_list   *next;
}   t_list;

int     ft_isalpha(int c);
int     ft_isdigit(int c);
int     ft_isalnum(int c);
int     ft_isascii(int c);
int     ft_isprint(int c);
size_t  ft_strlen(const char *c);
int     ft_tolower(int c);
int     ft_toupper(int c);
int     ft_strncmp(const char *s1, const char *s2, size_t n);
void    *ft_memset(void *b, int c, size_t len);
void    ft_bzero(void *s, size_t n);
void    *ft_memcpy(void *dst, const void *src, size_t n);
void    *ft_memmove(void *dst, const void *src, size_t len);
size_t  ft_strlcpy(char *dst, const char *src, size_t dstsize);
size_t  ft_strlcat(char *dst, const char *src, size_t dstsize);
char    *ft_strchr(const char *s, int c);
char    *ft_strrchr(const char *s, int c);

#endif /* LIBFT_H */
```

#### Visual Explanation
1. **Initial Check**:
   - `#ifndef LIBFT_H`: Checks if `LIBFT_H` is not defined.
2. **Define Header**:
   - `#define LIBFT_H`: Defines `LIBFT_H` to prevent future inclusions.
3. **Include Content**:
   - The content of the header file is included.
4. **End of Guard**:
   - `#endif`: Marks the end of the include guard.

#### Situations Where `#ifndef` and `#define` are Useful
- **Preventing Multiple Inclusions**: Ensures that the header file is included only once, avoiding redefinition errors.
- **Improving Compilation Time**: Reduces compilation time by preventing redundant processing of the same header file.
- **Maintaining Code Consistency**: Helps maintain consistency by ensuring that the header file's content is included only once.

### Function Manual: 
`typedef struct s_list`

#### Overview
The `typedef struct s_list` defines a structure for a singly linked list node and creates an alias `t_list` for it.

#### Syntax
```c
typedef struct s_list
{
    void            *content;
    struct s_list   *next;
}   t_list;
```

#### Detailed Explanation
The structure performs the following steps:
1. **Define Structure**: `struct s_list` is defined with two members:
   - `void *content`: A pointer to the content of the node.
   - `struct s_list *next`: A pointer to the next node in the list.
2. **Create Alias**: `typedef` creates an alias `t_list` for `struct s_list`.

#### Code Example
```c
typedef struct s_list
{
    void            *content;
    struct s_list   *next;
}   t_list;
```


#### Visual Explanation
1. **Define Structure**:
   - `struct s_list` is defined with `void *content` and `struct s_list *next`.
2. **Create Alias**:
   - `typedef` creates an alias `t_list` for `struct s_list`.
3. **Create Nodes**:
   - `node1` and `node2` are created using `ft_lstnew`.
4. **Link Nodes**:
   - `node1->next` is set to `node2`.
5. **Traverse List**:
   - The list is traversed, and the content of each node is printed.

#### Situations Where `typedef struct s_list` is Useful
- **Linked List Implementation**: Defining nodes for a singly linked list.
- **Dynamic Data Structures**: Managing dynamic data structures that require linked nodes.
- **Data Processing**: Storing and processing data in a sequential manner using linked nodes.