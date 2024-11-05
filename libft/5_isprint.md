### Function Manual: 

ft_isprint

#### Overview
The ft_isprint function checks if a given character is printable (i.e., it is a character that occupies a printing position on the screen).

#### Function Prototype
```c
int ft_isprint(int c);
```

#### Parameters
- c: The character to be checked, passed as an integer.

#### Return Value
- Returns the character itself if it is printable.
- Returns `0` if the character is not printable.

#### Detailed Explanation
The function uses ASCII values to determine if the character is printable:
- It checks if the character is between 32 (space) and 126 (tilde `~`).

#### Code
```c
#include "libft.h"

int	ft_isprint(int c)
{
	if (c >= 32 && c <= 126)
		return (c);
	return (0);
}
```

#### Usage Example
Here is an example of how to use the ft_isprint function:
```c
#include <stdio.h>
#include <ctype.h>
#include "libft.h"

int main(void)
{
	int test_chars[] = {31, 32, 48, 65, 90, 97, 122, 126, 127};
	int num_tests = sizeof(test_chars) / sizeof(test_chars[0]);

	for (int i = 0; i < num_tests; i++)
	{
		int c = test_chars[i];
		printf("ft_isprint(%d) = %d\n", c, ft_isprint(c));
		printf("isprint(%d) = %d\n", c, isprint(c));
	}

	return 0;
}
```

#### Visual Explanation
1. **Input Character: 31**
   - ASCII value: 31
   - Check: 31 is not between 32 and 126
   - Result: Returns 0 (false)
2. **Input Character: 32**
   - ASCII value: 32
   - Check: 32 is between 32 and 126
   - Result: Returns 32 (true)
3. **Input Character: 48**
   - ASCII value: 48
   - Check: 48 is between 32 and 126
   - Result: Returns 48 (true)
4. **Input Character: 65**
   - ASCII value: 65
   - Check: 65 is between 32 and 126
   - Result: Returns 65 (true)
5. **Input Character: 90**
   - ASCII value: 90
   - Check: 90 is between 32 and 126
   - Result: Returns 90 (true)
6. **Input Character: 97**
   - ASCII value: 97
   - Check: 97 is between 32 and 126
   - Result: Returns 97 (true)
7. **Input Character: 122**
   - ASCII value: 122
   - Check: 122 is between 32 and 126
   - Result: Returns 122 (true)
8. **Input Character: 126**
   - ASCII value: 126
   - Check: 126 is between 32 and 126
   - Result: Returns 126 (true)
9. **Input Character: 127**
   - ASCII value: 127
   - Check: 127 is not between 32 and 126
   - Result: Returns 0 (false)

#### Situations Where ft_isprint is Useful
- **Input Validation**: Ensuring that user input consists only of printable characters.
- **Parsing Text**: Identifying and processing printable characters in text processing applications.
- **Data Sanitization**: Filtering out non-printable characters from data to ensure it is suitable for display or further processing.