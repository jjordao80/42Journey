### Function Manual: 

ft_tolower

#### Overview
The ft_tolower function converts an uppercase alphabetic character to its corresponding lowercase character.

#### Function Prototype
```c
int ft_tolower(int c);
```

#### Parameters
- c: The character to be converted, passed as an integer.

#### Return Value
- Returns the lowercase equivalent of the character if it is an uppercase alphabetic character.
- Returns the character itself if it is not an uppercase alphabetic character.

#### Detailed Explanation
The function checks if the character is between 'A' and 'Z' (uppercase letters). If it is, it converts the character to its lowercase equivalent by adding 32 to its ASCII value.

#### Code
```c
#include "libft.h" 

int	ft_tolower(int c)
{
	if (c >= 'A' && c <= 'Z')
	{
		return (c + 32);
	}
	return (c);
}
```

#### Usage Example
Here is an example of how to use the ft_tolower function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char c = 'A';
	printf("ft_tolower(%c) = %c\n", c, ft_tolower(c));
	return 0;
}
```

#### Visual Explanation
1. **Input Character: 'A'**
   - **Step 1**: Check if 'A' is between 'A' and 'Z'.
     - 'A' is between 'A' and 'Z'.
   - **Step 2**: Convert 'A' to lowercase by adding 32 to its ASCII value.
     - ASCII value of 'A' is 65.
     - 65 + 32 = 97.
     - ASCII value 97 corresponds to 'a'.
   - **Step 3**: Return 'a'.

2. **Input Character: 'b'**
   - **Step 1**: Check if 'b' is between 'A' and 'Z'.
     - 'b' is not between 'A' and 'Z'.
   - **Step 2**: Return 'b' as it is.

#### Situations Where ft_tolower is Useful
- **Text Processing**: Converting text to lowercase for case-insensitive comparisons.
- **Input Validation**: Ensuring that user input is in lowercase.
- **Data Sanitization**: Converting all uppercase characters in a dataset to lowercase for consistency.
- **String Manipulation**: Preparing strings for display or further processing where lowercase is required.