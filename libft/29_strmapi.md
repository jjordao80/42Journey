### Function Manual: 

ft_strmapi

#### Overview
The ft_strmapi function applies a given function to each character of a string, passing the character's index as the first argument to create a new string.

#### Function Prototype
```c
char *ft_strmapi(char const *s, char (*f)(unsigned int, char));
```

#### Parameters
- s: The original string to be processed.
- f: A function that takes an unsigned integer (the index) and a character, and returns a character.

#### Return Value
- Returns a pointer to the newly allocated string resulting from the successive applications of f.
- Returns `NULL` if the allocation fails.

#### Detailed Explanation
The function performs the following steps:
1. **Memory Allocation**: Allocates memory for the new string, including space for the null terminator.
2. **Null Check**: Checks if the allocation was successful. If not, returns `NULL`.
3. **Apply Function**: Iterates through the original string, applying the function f to each character and storing the result in the new string.
4. **Null Termination**: Adds a null terminator at the end of the new string.
5. **Return Result**: Returns the newly allocated string.

#### Code
```c
#include "libft.h"

char	*ft_strmapi(char const *s, char (*f)(unsigned int, char))
{
	char	*new_str;
	size_t	i;

	new_str = malloc(ft_strlen(s) + 1);
	if (!new_str)
		return (NULL);
	i = 0;
	while (s[i])
	{
		new_str[i] = f(i, s[i]);
		i++;
	}
	new_str[i] = '\0';
	return (new_str);
}
```

#### Usage Example
Here is an example of how to use the ft_strmapi function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    char *str = "hello, world!";
    char *result = ft_strmapi(str, ft_toupper);
    printf("Original: %s\n", str);
    printf("Modified: %s\n", result);
    free(result);
    return 0;
}
```

### Visual Explanation
1. **Input String: "hello, world!"**
   - **Step 1**: Allocate memory for the new string.
     - `new_str = malloc(14)` (13 characters + 1 null terminator).
   - **Step 2**: Check if the allocation was successful.
     - Allocation is successful, so continue.
   - **Step 3**: Iterate through the original string and apply the function f.
     - `i = 0`, s[0] is 'h', f(0, 'h') returns 'H', `new_str[0]` is 'H'.
     - `i = 1`, s[1] is 'e', f(1, 'e') returns 'E', `new_str[1]` is 'E'.
     - `i = 2`, s[2] is 'l', f(2, 'l') returns 'L', `new_str[2]` is 'L'.
     - Continue this process for each character in the string.
   - **Step 4**: Null-terminate the new string.
     - `new_str[13] = '\0'`.
   - **Step 5**: Return the new string.
     - Return `new_str`.

### Situations Where ft_strmapi is Useful
- **String Transformation**: Applying transformations to each character of a string based on its position.
- **Text Processing**: Modifying text data by applying functions to each character.
- **Custom Encoding**: Creating custom encoded strings by applying specific functions to each character.
- **Data Sanitization**: Applying sanitization functions to each character of a string to ensure data integrity.
