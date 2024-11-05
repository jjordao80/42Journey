### Function Manual: 

ft_strchr

#### Overview
The ft_strchr function locates the first occurrence of a character in a string.

#### Function Prototype
```c
char *ft_strchr(const char *s, int c);
```

#### Parameters
- s: The string to be searched.
- c: The character to be located, passed as an `int` but internally treated as a `char`.

#### Return Value
- Returns a pointer to the first occurrence of the character c in the string s.
- Returns `NULL` if the character is not found.

#### Detailed Explanation
The function iterates through the string s and checks each character to see if it matches c. If a match is found, it returns a pointer to the matching character in the string. If the character c is the null-terminating character (`'\0'`), the function returns a pointer to the null terminator at the end of the string. If the character is not found, the function returns `NULL`.

#### Code
```c
#include "libft.h"

char *ft_strchr(const char *s, int c)
{
    int i;

    i = 0;
    while (s[i] != '\0')
    {
        if (s[i] == (char)c)
            return ((char *)&s[i]);
        i++;
    }
    if ((unsigned char)c == '\0')
        return ((char *)&s[i]);
    return (NULL);
}
```

#### Usage Example
Here is an example of how to use the ft_strchr function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    const char *str = "Hello, World!";
    char ch = 'W';
    char *result = ft_strchr(str, ch);

    if (result)
        printf("Character '%c' found at position: %ld\n", ch, result - str);
    else
        printf("Character '%c' not found.\n", ch);

    return 0;
}
```

#### Visual Explanation
1. **Input String: "Hello, World!"**
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Check if s[i] is not null (`'\0'`).
     - s[0] is 'H' (not null), check if it matches c ('W'). It doesn't, increment `i` to 1.
     - s[1] is 'e' (not null), check if it matches c ('W'). It doesn't, increment `i` to 2.
     - s[2] is 'l' (not null), check if it matches c ('W'). It doesn't, increment `i` to 3.
     - s[3] is 'l' (not null), check if it matches c ('W'). It doesn't, increment `i` to 4.
     - s[4] is 'o' (not null), check if it matches c ('W'). It doesn't, increment `i` to 5.
     - s[5] is ',' (not null), check if it matches c ('W'). It doesn't, increment `i` to 6.
     - s[6] is ' ' (not null), check if it matches c ('W'). It doesn't, increment `i` to 7.
     - s[7] is 'W' (not null), check if it matches c ('W'). It does, return a pointer to s[7].
   - **Step 3**: If c is the null-terminating character (`'\0'`), return a pointer to the null terminator.
   - **Step 4**: If no match is found, return `NULL`.

#### Situations Where ft_strchr is Useful
- **String Parsing**: Finding the position of a specific character in a string for parsing purposes.
- **Input Validation**: Checking if a string contains a specific character.
- **Text Processing**: Locating characters in text processing applications.
- **Tokenization**: Identifying delimiters in a string for tokenization.