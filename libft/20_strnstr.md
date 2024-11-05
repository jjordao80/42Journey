### Function Manual: 

ft_strnstr

#### Overview
The ft_strnstr function locates the first occurrence of the null-terminated string `needle` in the string `haystack`, where not more than len characters are searched.

#### Function Prototype
```c
char *ft_strnstr(const char *haystack, const char *needle, size_t len);
```

#### Parameters
- `haystack`: The string to be searched.
- `needle`: The substring to be located.
- len: The maximum number of characters to be searched.

#### Return Value
- Returns a pointer to the first occurrence of `needle` in `haystack`.
- Returns `NULL` if `needle` is not found within the first len characters of `haystack`.

#### Detailed Explanation
The function iterates through the `haystack` string and checks if the `needle` string matches any substring within the first len characters. If a match is found, it returns a pointer to the beginning of the match in `haystack`. If no match is found, it returns `NULL`.

#### Code
```c
#include "libft.h"

char	*ft_strnstr(const char *haystack, const char *needle, size_t len)
{
	size_t	i;
	size_t	j;

	i = 0;
	j = 0;
	if (needle[0] == 0)
		return ((char *) haystack);
	while (haystack[i] && i < len)
	{
		while (haystack[i + j] == needle[j] && haystack[i + j] && i + j < len)
			j++;
		if (needle[j] == 0)
			return ((char *) haystack + i);
		i++;
		j = 0;
	}
	return (0);
}
```

#### Usage Example
Here is an example of how to use the ft_strnstr function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    const char *haystack = "Hello, World!";
    const char *needle = "World";
    size_t len = 12;
    char *result = ft_strnstr(haystack, needle, len);
    if (result)
        printf("Found '%s' in '%s': %s\n", needle, haystack, result);
    else
        printf("'%s' not found in '%s' within the first %zu characters.\n", needle, haystack, len);
    return 0;
}
```

### Visual Explanation

1. **Input Strings**: 
   - `haystack`: "Hello, World!"
   - `needle`: "World"
   - `len`: 12

2. **Step-by-Step Process**:

   - **Step 1**: Initialize `i` to 0 and `j` to 0.
     - `i = 0`
     - `j = 0`

   - **Step 2**: Check if `needle` is an empty string.
     - If `needle` is empty, return `haystack`.
     - In this case, `needle` is not empty, so proceed to the next step.

   - **Step 3**: Iterate through `haystack` while `i` is less than `len`.
     - **Iteration 1** (`i = 0`):
       - Compare `haystack[0]` ('H') with `needle[0]` ('W'):
         - They do not match, so increment `i` and reset `j` to 0.
       - `i = 1`
       - `j = 0`
     - **Iteration 2** (`i = 1`):
       - Compare `haystack[1]` ('e') with `needle[0]` ('W'):
         - They do not match, so increment `i` and reset `j` to 0.
       - `i = 2`
       - `j = 0`
     - **Iteration 3** (`i = 2`):
       - Compare `haystack[2]` ('l') with `needle[0]` ('W'):
         - They do not match, so increment `i` and reset `j` to 0.
       - `i = 3`
       - `j = 0`
     - **Iteration 4** (`i = 3`):
       - Compare `haystack[3]` ('l') with `needle[0]` ('W'):
         - They do not match, so increment `i` and reset `j` to 0.
       - `i = 4`
       - `j = 0`
     - **Iteration 5** (`i = 4`):
       - Compare `haystack[4]` ('o') with `needle[0]` ('W'):
         - They do not match, so increment `i` and reset `j` to 0.
       - `i = 5`
       - `j = 0`
     - **Iteration 6** (`i = 5`):
       - Compare `haystack[5]` (',') with `needle[0]` ('W'):
         - They do not match, so increment `i` and reset `j` to 0.
       - `i = 6`
       - `j = 0`
     - **Iteration 7** (`i = 6`):
       - Compare `haystack[6]` (' ') with `needle[0]` ('W'):
         - They do not match, so increment `i` and reset `j` to 0.
       - `i = 7`
       - `j = 0`
     - **Iteration 8** (`i = 7`):
       - Compare `haystack[7]` ('W') with `needle[0]` ('W'):
         - They match, so increment `j`.
       - `i = 7`
       - `j = 1`
       - Compare `haystack[8]` ('o') with `needle[1]` ('o'):
         - They match, so increment `j`.
       - `i = 7`
       - `j = 2`
       - Compare `haystack[9]` ('r') with `needle[2]` ('r'):
         - They match, so increment `j`.
       - `i = 7`
       - `j = 3`
       - Compare `haystack[10]` ('l') with `needle[3]` ('l'):
         - They match, so increment `j`.
       - `i = 7`
       - `j = 4`
       - Compare `haystack[11]` ('d') with `needle[4]` ('d'):
         - They match, so increment `j`.
       - `i = 7`
       - `j = 5`
       - `needle[j]` is now the null-terminator, so return `haystack + i` which points to "World!".

   - **Step 4**: If no match is found, return `NULL`.

#### Summary
- The function successfully finds the substring "World" within the first 12 characters of "Hello, World!" and returns a pointer to the beginning of the match in `haystack`.

#### Situations Where ft_strnstr is Useful
- **Substring Search**: Finding a substring within a string up to a specified length.
- **Input Validation**: Checking if a specific pattern exists within user input.
- **Text Processing**: Locating specific keywords or phrases within a text.
- **Data Parsing**: Identifying and extracting specific data from a larger dataset.