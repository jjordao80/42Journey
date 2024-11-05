### Function Manual: 

ft_isalnum

#### Overview
The ft_isalnum function checks if a given character is alphanumeric (either a digit or an alphabetic letter).

#### Function Prototype
```c
int ft_isalnum(int c);
```

#### Parameters
- c: The character to be checked, passed as an integer.

#### Return Value
- Returns the character itself if it is alphanumeric.
- Returns `0` if the character is not alphanumeric.

#### Detailed Explanation
The function uses ASCII values to determine if the character is alphanumeric:
- It checks if the character is between '0' and '9' (digits).
- It checks if the character is between 'A' and 'Z' (uppercase letters).
- It checks if the character is between 'a' and 'z' (lowercase letters).

#### Code
```c
#include "libft.h"

int ft_isalnum(int c)
{
    if ((c >= 48 && c <= 57) || (c >= 65 && c <= 90) || (c >= 97 && c <= 122))
        return (c);
    return (0);
}
```

#### Usage Example
Here is an example of how to use the ft_isalnum function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    int test_chars[] = {'0', '9', 'A', 'Z', 'a', 'z', '!', ' ', '1', 'b'};
    int num_tests = sizeof(test_chars) / sizeof(test_chars[0]);
    
    for (int i = 0; i < num_tests; i++)
    {
        int result = ft_isalnum(test_chars[i]);
        printf("ft_isalnum('%c') = %d\n", test_chars[i], result);
    }
    
    return 0;
}
```

#### Visual Explanation
1. **Input Character: '0'**
   - ASCII value: 48
   - Check: 48 is between 48 ('0') and 57 ('9')
   - Result: Returns 48 (true)

2. **Input Character: '9'**
   - ASCII value: 57
   - Check: 57 is between 48 ('0') and 57 ('9')
   - Result: Returns 57 (true)

3. **Input Character: 'A'**
   - ASCII value: 65
   - Check: 65 is between 65 ('A') and 90 ('Z')
   - Result: Returns 65 (true)

4. **Input Character: 'Z'**
   - ASCII value: 90
   - Check: 90 is between 65 ('A') and 90 ('Z')
   - Result: Returns 90 (true)

5. **Input Character: 'a'**
   - ASCII value: 97
   - Check: 97 is between 97 ('a') and 122 ('z')
   - Result: Returns 97 (true)

6. **Input Character: 'z'**
   - ASCII value: 122
   - Check: 122 is between 97 ('a') and 122 ('z')
   - Result: Returns 122 (true)

7. **Input Character: '!'**
   - ASCII value: 33
   - Check: 33 is not between 48 and 57, nor between 65 and 90, nor between 97 and 122
   - Result: Returns 0 (false)

8. **Input Character: ' '**
   - ASCII value: 32
   - Check: 32 is not between 48 and 57, nor between 65 and 90, nor between 97 and 122
   - Result: Returns 0 (false)

9. **Input Character: '1'**
   - ASCII value: 49
   - Check: 49 is between 48 ('0') and 57 ('9')
   - Result: Returns 49 (true)

10. **Input Character: 'b'**
    - ASCII value: 98
    - Check: 98 is between 97 ('a') and 122 ('z')
    - Result: Returns 98 (true)

#### Situations Where ft_isalnum is Useful
- **Input Validation**: Ensuring that user input consists only of alphanumeric characters.
- **Parsing Text**: Identifying and processing alphanumeric characters in text processing applications.
- **Tokenization**: Separating alphanumeric tokens from non-alphanumeric ones in lexical analysis.