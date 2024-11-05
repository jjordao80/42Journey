### Function Manual: 

ft_substr

#### Overview
The ft_substr function extracts a substring from a given string, starting at a specified position and with a specified length.

#### Function Prototype
```c
char *ft_substr(char const *s, unsigned int start, size_t len);
```

#### Parameters
- s: The original string from which the substring will be extracted.
- start: The starting position of the substring within the original string.
- len: The length of the substring to be extracted.

#### Return Value
- Returns a pointer to the newly allocated substring.
- Returns `NULL` if the allocation fails or if the input string is `NULL`.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if the input string s is `NULL`. If it is, returns `NULL`.
2. **Start Position Check**: Checks if the start position is greater than or equal to the length of the string s. If it is, returns an empty string.
3. **Memory Allocation**: Allocates memory for the substring, including space for the null terminator.
4. **Substring Extraction**: Copies characters from the original string s to the substring until the specified length len is reached or the end of the string is encountered.
5. **Null Termination**: Adds a null terminator to the end of the substring.
6. **Return Result**: Returns the newly allocated substring.

#### Code
```c
#include "libft.h"
char	*ft_substr(char const *s, unsigned int start, size_t len)
{
	size_t	i;
	char	*substr;
	char	*result;

	if (!s)
		return (NULL);
	if (start >= ft_strlen(s))
		return (ft_strdup(""));
	substr = (char *)malloc(sizeof(char) * (len + 1));
	if (!substr)
		return (NULL);
	i = 0;
	while (i < len && s[start + i])
	{
		substr[i] = s[start + i];
		i++;
	}
	substr[i] = '\0';
	result = ft_strdup(substr);
	free(substr);
	return (result);
}
```

#### Usage Example
Here is an example of how to use the ft_substr function:
```c
#include <stdio.h>
#include <stdlib.h>
#include "libft.h"

int main()
{
	char *str = "Hello, World!";
	unsigned int start = 7;
	size_t len = 5;
	char *result = ft_substr(str, start, len);
	
	printf("ft_substr(\"%s\", %u, %zu) = %s\n", str, start, len, result);
	free(result);
	return 0;
}
```

#### Visual Explanation
1. **Input String: "Hello, World!"**
   - **Step 1**: Check if the input string s is `NULL`.
     - s is not `NULL`, so continue.
   - **Step 2**: Check if the start position is greater than or equal to the length of s.
     - start is 7, and the length of s is 13, so continue.
   - **Step 3**: Allocate memory for the substring.
     - `substr = malloc(6)` (5 characters + 1 null terminator).
   - **Step 4**: Copy characters from s to `substr`.
     - Copy 'W' to `substr[0]`
     - Copy 'o' to `substr[1]`
     - Copy 'r' to `substr[2]`
     - Copy 'l' to `substr[3]`
     - Copy 'd' to `substr[4]`
   - **Step 5**: Null-terminate `substr`.
     - `substr[5] = '\0'`
   - **Step 6**: Duplicate the substring and free the original allocation.
     - `result = ft_strdup(substr)`
     - `free(substr)`
   - **Step 7**: Return the result.
     - Return `result`

2. **Final Memory Areas**:
   - Original string s: "Hello, World!"
   - Substring `result`: "World"

#### Situations Where ft_substr is Useful
- **String Manipulation**: Extracting a portion of a string for further processing or analysis.
- **Text Processing**: Extracting specific parts of text data, such as words or phrases.
- **Data Parsing**: Parsing and extracting substrings from structured data formats.
- **Buffer Management**: Creating smaller buffers from larger strings for efficient memory usage.
