### Function Manual: 

ft_strtrim

#### Overview
The ft_strtrim function removes all leading and trailing characters from the string s1 that are present in the string set.

#### Function Prototype
```c
char *ft_strtrim(char const *s1, char const *set);
```

#### Parameters
- s1: The original string to be trimmed.
- set: The set of characters to be removed from the beginning and end of s1.

#### Return Value
- Returns a pointer to the newly allocated trimmed string.
- Returns `NULL` if the allocation fails or if either s1 or set is `NULL`.

#### Detailed Explanation
The function performs the following steps:
1. **Null Check**: Checks if either s1 or set is `NULL`. If either is `NULL`, returns `NULL`.
2. **Find Start Position**: Iterates through s1 from the beginning to find the first character not in set.
3. **Find End Position**: Iterates through s1 from the end to find the last character not in set.
4. **Extract Substring**: Uses ft_substr to create a new string from s1 starting at start and ending at `end`.
5. **Return Result**: Returns the newly allocated trimmed string.

#### Code
```c
#include "libft.h"

char	*ft_strtrim(char const *s1, char const *set)
{
	size_t	start;
	size_t	end;
	char	*str;

	if (!s1 || !set)
		return (NULL);
	start = 0;
	while (s1[start] && ft_strchr(set, s1[start]))
		start++;
	end = ft_strlen(s1);
	while (end > start && ft_strchr(set, s1[end - 1]))
		end--;
	str = ft_substr(s1, start, end - start);
	if (!str)
		return (NULL);
	return (str);
}
```

#### Usage Example
Here is an example of how to use the ft_strtrim function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    char *s1 = "  Hello, World!  ";
    char *set = " ";
    char *trimmed = ft_strtrim(s1, set);
    if (trimmed)
    {
        printf("Original: '%s'\n", s1);
        printf("Trimmed: '%s'\n", trimmed);
        free(trimmed);
    }
    else
    {
        printf("Memory allocation failed.\n");
    }
    return 0;
}
```

### Visual Explanation

1. **Input Parameters**:
   - `s1`: "  Hello, World!  "
   - `set`: " "

2. **Step-by-Step Process**:

   - **Step 1**: Check if `s1` or `set` is `NULL`.
     - Both are not `NULL`, so continue.

   - **Step 2**: Find the start position.
     - `s1[0]` is ' ' (in `set`), increment `start` to 1.
     - `s1[1]` is ' ' (in `set`), increment `start` to 2.
     - `s1[2]` is 'H' (not in `set`), stop.
     - `start` is 2.

   - **Step 3**: Find the end position.
     - `s1[15]` is ' ' (in `set`), decrement `end` to 15.
     - `s1[14]` is ' ' (in `set`), decrement `end` to 14.
     - `s1[13]` is '!' (not in `set`), stop.
     - `end` is 14.

   - **Step 4**: Extract the substring.
     - Call `ft_substr(s1, 2, 14 - 2)` which results in "Hello, World!".

   - **Step 5**: Return the trimmed string.
     - Return "Hello, World!".

3. **Final Memory Areas**:
   - `s1`: "  Hello, World!  "
   - `set`: " "
   - `trimmed`: "Hello, World!"

#### Visual Representation

```plaintext
Initial String (s1): "  Hello, World!  "
Set of Characters to Trim (set): " "

Step 2: Find the start position
s1: "  Hello, World!  "
     ^  ^
     |  |
     |  Start position moves past spaces
     Start position is 2 (character 'H')

Step 3: Find the end position
s1: "  Hello, World!  "
                   ^  ^
                   |  |
                   |  End position moves past spaces
                   End position is 14 (character '!')

Step 4: Extract the substring
Substring from position 2 to 14: "Hello, World!"

Step 5: Return the trimmed string
Trimmed String: "Hello, World!"
```

#### Situations Where `ft_strtrim` is Useful
- **Input Sanitization**: Removing unwanted characters from user input.
- **Text Processing**: Cleaning up strings by removing leading and trailing whitespace or other characters.
- **Data Parsing**: Preparing strings for parsing by trimming unnecessary characters.
- **Formatting Output**: Ensuring that strings are properly formatted by removing extraneous characters.
