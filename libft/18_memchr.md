### Function Manual: 

ft_memchr

#### Overview
The ft_memchr function locates the first occurrence of a character in a block of memory.

#### Function Prototype
```c
void *ft_memchr(const void *s, int c, size_t n);
```

#### Parameters
- s: A pointer to the block of memory to be searched.
- c: The character to be located, passed as an `int` but internally treated as an `unsigned char`.
- n: The number of bytes to be analyzed.

#### Return Value
- Returns a pointer to the first occurrence of the character c in the block of memory.
- Returns `NULL` if the character is not found within the first n bytes.

#### Detailed Explanation
The function iterates through the memory block pointed to by s and checks each byte to see if it matches the character c. If a match is found, it returns a pointer to the matching byte. If no match is found within the first n bytes, the function returns `NULL`.

#### Code
```c
#include "libft.h"

void	*ft_memchr(const void *s, int c, size_t n)
{
	size_t	i;

	i = 0;
	while (i < n)
	{
		if (((unsigned char *)s)[i] == (unsigned char)c)
			return ((void *)(s + i));
		i++;
	}
	return (NULL);
}
```

#### Usage Example
Here is an example of how to use the ft_memchr function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char str[] = "Hello, World!";
	char c = 'o';
	char *result = ft_memchr(str, c, sizeof(str));
	if (result != NULL)
		printf("Character '%c' found at position: %ld\n", c, result - str);
	else
		printf("Character '%c' not found\n", c);
	return 0;
}
```

#### Visual Explanation
1. **Input Memory Block**: "Hello, World!"
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Check if `i` is less than n (13 in this case).
   - **Step 3**: Compare the byte at s[i] with c.
     - s[0] is 'H' (not 'o'), increment `i` to 1.
     - s[1] is 'e' (not 'o'), increment `i` to 2.
     - s[2] is 'l' (not 'o'), increment `i` to 3.
     - s[3] is 'l' (not 'o'), increment `i` to 4.
     - s[4] is 'o' (matches 'o'), return a pointer to s[4].
   - **Step 4**: If no match is found within the first n bytes, return `NULL`.

#### Situations Where ft_memchr is Useful
- **Searching in Buffers**: Finding a specific byte in a buffer or memory block.
- **Data Parsing**: Locating delimiters or specific markers in binary data.
- **Memory Analysis**: Analyzing memory content for debugging or validation purposes.
- **String Manipulation**: Finding characters in strings when working with raw memory.