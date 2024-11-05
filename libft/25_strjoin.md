### Function Manual: 

ft_strjoin

#### Overview
The ft_strjoin function concatenates two strings, s1 and s2, into a new string.

#### Function Prototype
```c
char *ft_strjoin(char const *s1, char const *s2);
```

#### Parameters
- s1: The first string to be concatenated.
- s2: The second string to be concatenated.

#### Return Value
- Returns a pointer to the newly allocated string that contains the concatenation of s1 and s2.
- Returns `NULL` if the allocation fails or if either s1 or s2 is `NULL`.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if either s1 or s2 is `NULL`. If either is `NULL`, returns `NULL`.
2. **Memory Allocation**: Allocates memory for the new string, which is the combined length of s1 and s2 plus one for the null terminator.
3. **Copy First String**: Copies the characters from s1 to the new string.
4. **Copy Second String**: Copies the characters from s2 to the new string, starting where s1 ended.
5. **Null Termination**: Adds a null terminator at the end of the new string.
6. **Return Result**: Returns the newly allocated string.

#### Code
```c
#include "libft.h"

char	*ft_strjoin(char const *s1, char const *s2)
{
	char	*str;
	size_t	i;
	size_t	j;

	if (!s1 || !s2)
		return (NULL);
	str = (char *)malloc(sizeof(char) * (ft_strlen(s1) + ft_strlen(s2) + 1));
	if (!str)
		return (NULL);
	i = 0;
	j = 0;
	while (s1[i])
	{
		str[i] = s1[i];
		i++;
	}
	while (s2[j])
	{
		str[i + j] = s2[j];
		j++;
	}
	str[i + j] = '\0';
	return (str);
}
```

#### Usage Example
Here is an example of how to use the ft_strjoin function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    char *s1 = "Hello, ";
    char *s2 = "World!";
    char *result = ft_strjoin(s1, s2);
    if (result)
    {
        printf("Concatenated string: %s\n", result);
        free(result);
    }
    else
    {
        printf("Memory allocation failed.\n");
    }
    return 0;
}
```

#### Visual Explanation
1. **Input Strings**:
   - s1: "Hello, "
   - s2: "World!"
2. **Step-by-Step Process**:
   - **Step 1**: Check if s1 or s2 is `NULL`.
     - Both are not `NULL`, so continue.
   - **Step 2**: Allocate memory for the new string.
     - str = malloc(14) (7 characters from s1 + 6 characters from s2 + 1 null terminator).
   - **Step 3**: Copy characters from s1 to str.
     - Copy 'H' to str[0]
     - Copy 'e' to str[1]
     - Copy 'l' to str[2]
     - Copy 'l' to str[3]
     - Copy 'o' to str[4]
     - Copy ',' to str[5]
     - Copy ' ' to str[6]
   - **Step 4**: Copy characters from s2 to str.
     - Copy 'W' to str[7]
     - Copy 'o' to str[8]
     - Copy 'r' to str[9]
     - Copy 'l' to str[10]
     - Copy 'd' to str[11]
     - Copy '!' to str[12]
   - **Step 5**: Null-terminate str.
     - str[13] = '\0'
   - **Step 6**: Return the pointer to the new string.
     - Return str
3. **Final Memory Areas**:
   - s1: "Hello, "
   - s2: "World!"
   - str: "Hello, World!"

#### Situations Where ft_strjoin is Useful
- **String Concatenation**: When you need to concatenate two strings into a new string.
- **Dynamic String Building**: Building a new string from multiple parts dynamically.
- **Text Processing**: Combining multiple strings in text processing applications.
- **Buffer Management**: Creating a single buffer from multiple string sources.
