### Function Manual: 

ft_isascii

#### Overview
The ft_isascii function checks if a given character is an ASCII character (i.e., its value is between 0 and 127 inclusive).

#### Function Prototype
```c
int ft_isascii(int c);
```

#### Parameters
- c: The character to be checked, passed as an integer.

#### Return Value
- Returns `1` if the character is an ASCII character.
- Returns `0` if the character is not an ASCII character.

#### Detailed Explanation
The function uses the ASCII values to determine if the character is within the ASCII range:
- It checks if the character is between 0 and 127.

#### Code
```c
#include "libft.h"

int ft_isascii(int c)
{
    if (c >= 0 && c <= 127)
        return (1);
    return (0);
}
```

#### Usage Example
Here is an example of how to use the ft_isascii function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    int test_chars[] = {65, 128, -1, 0, 127, 255};
    size_t num_tests = sizeof(test_chars) / sizeof(test_chars[0]);

    for (size_t i = 0; i < num_tests; i++)
    {
        int c = test_chars[i];
        printf("Testing character %d:\n", c);
        printf("ft_isascii: %d\n", ft_isascii(c));
    }
    return 0;
}
```

#### Visual Explanation
1. **Input Character: 65**
   - ASCII value: 65
   - Check: 65 is between 0 and 127
   - Result: Returns 1 (true)

2. **Input Character: 128**
   - ASCII value: 128
   - Check: 128 is not between 0 and 127
   - Result: Returns 0 (false)

3. **Input Character: -1**
   - ASCII value: -1
   - Check: -1 is not between 0 and 127
   - Result: Returns 0 (false)

4. **Input Character: 0**
   - ASCII value: 0
   - Check: 0 is between 0 and 127
   - Result: Returns 1 (true)

5. **Input Character: 127**
   - ASCII value: 127
   - Check: 127 is between 0 and 127
   - Result: Returns 1 (true)

6. **Input Character: 255**
   - ASCII value: 255
   - Check: 255 is not between 0 and 127
   - Result: Returns 0 (false)

#### Situations Where ft_isascii is Useful
- **Input Validation**: Ensuring that user input consists only of ASCII characters.
- **Parsing Text**: Identifying and processing ASCII characters in text processing applications.
- **Data Sanitization**: Filtering out non-ASCII characters from data to ensure compatibility with systems that only support ASCII.