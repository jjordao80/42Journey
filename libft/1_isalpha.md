### Function Manual: 

ft_isalpha

#### Overview
The ft_isalpha function checks if a given character is an alphabetic letter (either uppercase or lowercase).

#### Function Prototype
```c
int ft_isalpha(int c);
```

#### Parameters
- c: The character to be checked, passed as an integer.

#### Return Value
- Returns the character itself if it is an alphabetic letter.
- Returns `0` if the character is not an alphabetic letter.

#### Detailed Explanation
The function uses ASCII values to determine if the character is alphabetic:
- It checks if the character is between 'a' and 'z' (lowercase letters).
- It checks if the character is between 'A' and 'Z' (uppercase letters).

#### Code
```c
#include "libft.h"

int ft_isalpha(int c)
{
    if ((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z'))
        return (c);
    return (0);
}
```

#### Usage Example
Here is an example of how to use the ft_isalpha function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    char test_chars[] = {'a', 'z', 'A', 'Z', 'm', 'M', '1', '!', 0, -1, 128};
    int num_tests = sizeof(test_chars) / sizeof(test_chars[0]);

    for (int i = 0; i < num_tests; i++)
    {
        int result = ft_isalpha(test_chars[i]);
        printf("ft_isalpha(%d) = %d\n", test_chars[i], result);
    }

    return 0;
}
```

#### Visual Explanation
1. **Input Character: 'a'**
   - ASCII value: 97
   - Check: 97 is between 97 ('a') and 122 ('z')
   - Result: Returns 97 (true)

2. **Input Character: 'Z'**
   - ASCII value: 90
   - Check: 90 is between 65 ('A') and 90 ('Z')
   - Result: Returns 90 (true)

3. **Input Character: '1'**
   - ASCII value: 49
   - Check: 49 is not between 65 and 90, nor between 97 and 122
   - Result: Returns 0 (false)

#### Situations Where ft_isalpha is Useful
- **Input Validation**: Ensuring that user input consists only of alphabetic characters.
- **Parsing Text**: Identifying and processing alphabetic characters in text processing applications.
- **Tokenization**: Separating alphabetic tokens from non-alphabetic ones in lexical analysis.