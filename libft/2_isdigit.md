### Function Manual: 

ft_isdigit

#### Overview
The ft_isdigit function checks if a given character is a digit (0-9).

#### Function Prototype
```c
int ft_isdigit(int c);
```

#### Parameters
- c: The character to be checked, passed as an integer.

#### Return Value
- Returns the character itself if it is a digit.
- Returns `0` if the character is not a digit.

#### Detailed Explanation
The function uses ASCII values to determine if the character is a digit:
- It checks if the character is between '0' and '9'.

#### Code
```c
#include "libft.h"

int ft_isdigit(int c)
{
    if (c >= '0' && c <= '9')
        return (c);
    return (0);
}
```

#### Usage Example
Here is an example of how to use the ft_isdigit function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    int test_chars[] = {'0', '5', '9', 'a', 'Z', ' ', '!', '3', -1, 128};
    int num_tests = sizeof(test_chars) / sizeof(test_chars[0]);
    
    for (int i = 0; i < num_tests; i++)
    {
        int result = ft_isdigit(test_chars[i]);
        printf("ft_isdigit(%c) = %d\n", test_chars[i], result);
    }
    
    return 0;
}
```

#### Visual Explanation
1. **Input Character: '0'**
   - ASCII value: 48
   - Check: 48 is between 48 ('0') and 57 ('9')
   - Result: Returns 48 (true)

2. **Input Character: '5'**
   - ASCII value: 53
   - Check: 53 is between 48 ('0') and 57 ('9')
   - Result: Returns 53 (true)

3. **Input Character: '9'**
   - ASCII value: 57
   - Check: 57 is between 48 ('0') and 57 ('9')
   - Result: Returns 57 (true)

4. **Input Character: 'a'**
   - ASCII value: 97
   - Check: 97 is not between 48 and 57
   - Result: Returns 0 (false)

5. **Input Character: 'Z'**
   - ASCII value: 90
   - Check: 90 is not between 48 and 57
   - Result: Returns 0 (false)

6. **Input Character: ' '**
   - ASCII value: 32
   - Check: 32 is not between 48 and 57
   - Result: Returns 0 (false)

7. **Input Character: '!'**
   - ASCII value: 33
   - Check: 33 is not between 48 and 57
   - Result: Returns 0 (false)

8. **Input Character: '3'**
   - ASCII value: 51
   - Check: 51 is between 48 and 57
   - Result: Returns 51 (true)

9. **Input Character: -1**
   - ASCII value: -1
   - Check: -1 is not between 48 and 57
   - Result: Returns 0 (false)

10. **Input Character: 128**
    - ASCII value: 128
    - Check: 128 is not between 48 and 57
    - Result: Returns 0 (false)

#### Situations Where ft_isdigit is Useful
- **Input Validation**: Ensuring that user input consists only of numeric characters.
- **Parsing Text**: Identifying and processing numeric characters in text processing applications.
- **Tokenization**: Separating numeric tokens from non-numeric ones in lexical analysis.