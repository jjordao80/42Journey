### Function Manual: 

ft_strrchr

#### Overview
The ft_strrchr function locates the last occurrence of a character in a string.

#### Function Prototype
```c
char *ft_strrchr(const char *s, int c);
```

#### Parameters
- s: The string to be searched.
- c: The character to be located, passed as an `int` but internally treated as a `char`.

#### Return Value
- Returns a pointer to the last occurrence of the character c in the string s.
- Returns `NULL` if the character is not found.

#### Detailed Explanation
The function iterates through the string s and checks each character to see if it matches c. If a match is found, it updates the `last` pointer to point to the matching character. If the character c is the null-terminating character (`'\0'`), the function returns a pointer to the null terminator at the end of the string. If the character is not found, the function returns `NULL`.

#### Code
```c
#include "libft.h"

char	*ft_strrchr(const char *s, int c)
{
	const char	*last;

	last = NULL;
	while (*s != '\0')
	{
		if (*s == (char)c)
		{
			last = s;
		}
		s++;
	}
	if ((unsigned char)c == '\0')
		return ((char *)s);
	return ((char *)last);
}
```

#### Usage Example
Here is an example of how to use the ft_strrchr function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
	const char *str = "Hello, World!";
	char c = 'o';
	char *result = ft_strrchr(str, c);
	if (result)
		printf("The last occurrence of '%c' in \"%s\" is at position: %ld\n", c, str, result - str);
	else
		printf("Character '%c' not found in \"%s\"\n", c, str);
	return 0;
}
```

#### Visual Explanation
1. **Input String: "Hello, World!"**
   - **Step 1**: Initialize `last` to `NULL`.
   - **Step 2**: Iterate through each character of the string s.
     - s[0] is 'H' (not null), check if it matches c ('o'). It doesn't, move to the next character.
     - s[1] is 'e' (not null), check if it matches c ('o'). It doesn't, move to the next character.
     - s[2] is 'l' (not null), check if it matches c ('o'). It doesn't, move to the next character.
     - s[3] is 'l' (not null), check if it matches c ('o'). It doesn't, move to the next character.
     - s[4] is 'o' (not null), check if it matches c ('o'). It does, update `last` to point to s[4].
     - Continue this process until the end of the string.
   - **Step 3**: If c is the null-terminating character (`'\0'`), return a pointer to the null terminator.
   - **Step 4**: If no match is found, return `NULL`.
   - **Step 5**: Return the pointer `last`.

#### Situations Where ft_strrchr is Useful
- **String Parsing**: Finding the position of the last occurrence of a specific character in a string for parsing purposes.
- **Input Validation**: Checking if a string contains a specific character and finding its last occurrence.
- **Text Processing**: Locating characters in text processing applications.
- **Tokenization**: Identifying delimiters in a string for tokenization.