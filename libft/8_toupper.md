### Function Manual: 

ft_toupper

#### Overview
The ft_toupper function converts a lowercase alphabetic character to its corresponding uppercase character.

#### Function Prototype
```c
int ft_toupper(int c);
```

#### Parameters
- c: The character to be converted, passed as an integer.

#### Return Value
- Returns the uppercase equivalent of the character if it is a lowercase alphabetic character.
- Returns the character itself if it is not a lowercase alphabetic character.

#### Detailed Explanation
The function checks if the character is between 'a' and 'z' (lowercase letters). If it is, it converts the character to its uppercase equivalent by subtracting 32 from its ASCII value.

#### Code
```c
#include "libft.h" 

int	ft_toupper(int c)
{
	if (c >= 'a' && c <= 'z')
	{
		return (c - 32);
	}
	return (c);
}
```

#### Usage Example
Here is an example of how to use the ft_toupper function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char c = 'a';
	printf("ft_toupper(%c) = %c\n", c, ft_toupper(c));
	return 0;
}
```

#### Visual Explanation
1. **Input Character: 'a'**
   - **Step 1**: Check if 'a' is between 'a' and 'z'.
     - 'a' is between 'a' and 'z'.
   - **Step 2**: Convert 'a' to uppercase by subtracting 32 from its ASCII value.
     - ASCII value of 'a' is 97.
     - 97 - 32 = 65.
     - ASCII value 65 corresponds to 'A'.
   - **Step 3**: Return 'A'.

2. **Input Character: 'B'**
   - **Step 1**: Check if 'B' is between 'a' and 'z'.
     - 'B' is not between 'a' and 'z'.
   - **Step 2**: Return 'B' as it is.

#### Situations Where ft_toupper is Useful
- **Text Processing**: Converting text to uppercase for case-insensitive comparisons.
- **Input Validation**: Ensuring that user input is in uppercase.
- **Data Sanitization**: Converting all lowercase characters in a dataset to uppercase for consistency.