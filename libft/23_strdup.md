### Function Manual: 

ft_strdup

#### Overview
The ft_strdup function duplicates a given string by allocating memory for the new string and copying the content of the original string into it.

#### Function Prototype
```c
char *ft_strdup(const char *str);
```

#### Parameters
- str: The original string to be duplicated.

#### Return Value
- Returns a pointer to the newly allocated string containing the duplicate of the original string.
- Returns `NULL` if the memory allocation fails.

#### Detailed Explanation
The function performs the following steps:
1. **Memory Allocation**: Allocates memory for the new string, which is the length of the original string plus one for the null terminator.
2. **Null Check**: Checks if the allocation was successful. If not, returns `NULL`.
3. **String Copying**: Copies each character from the original string to the new string.
4. **Null-Termination**: Adds a null terminator at the end of the new string.
5. **Return Pointer**: Returns a pointer to the newly allocated and duplicated string.

#### Code
```c
#include "libft.h"

char	*ft_strdup(const char *str)
{
	size_t		i;
	char		*dest;

	dest = (char *) malloc(ft_strlen(str) + 1);
	if (!dest)
	{
		return (NULL);
	}
	i = 0;
	while (str[i] != '\0')
	{
		dest[i] = str[i];
		i++;
	}
	dest[i] = '\0';
	return (dest);
}
```

#### Usage Example
Here is an example of how to use the ft_strdup function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    char *original = "Hello, World!";
    char *duplicate = ft_strdup(original);

    if (duplicate)
    {
        printf("Original: %s\n", original);
        printf("Duplicate: %s\n", duplicate);
        free(duplicate);
    }
    else
    {
        printf("Memory allocation failed.\n");
    }

    return 0;
}
```

#### Visual Explanation
1. **Input String: "Hello, World!"**
   - **Step 1**: Allocate memory for the new string.
     - `dest = malloc(ft_strlen("Hello, World!") + 1)`
     - Memory allocated: 14 bytes (13 characters + 1 null terminator).
   - **Step 2**: Check if the allocation was successful.
     - If `dest` is `NULL`, return `NULL`.
   - **Step 3**: Copy each character from the original string to the new string.
     - Copy 'H' to `dest[0]`
     - Copy 'e' to `dest[1]`
     - Copy 'l' to `dest[2]`
     - Copy 'l' to `dest[3]`
     - Copy 'o' to `dest[4]`
     - Copy ',' to `dest[5]`
     - Copy ' ' to `dest[6]`
     - Copy 'W' to `dest[7]`
     - Copy 'o' to `dest[8]`
     - Copy 'r' to `dest[9]`
     - Copy 'l' to `dest[10]`
     - Copy 'd' to `dest[11]`
     - Copy '!' to `dest[12]`
   - **Step 4**: Null-terminate the new string.
     - `dest[13] = '\0'`
   - **Step 5**: Return the pointer to the new string.
     - Return `dest`

#### Situations Where ft_strdup is Useful
- **String Duplication**: Creating a copy of a string for manipulation without altering the original string.
- **Memory Management**: Allocating memory for a new string that is a duplicate of an existing string.
- **Data Processing**: Duplicating strings for processing in functions that modify the string content.
- **Buffer Management**: Creating a separate buffer with the same content as the original string for safe operations.