### Function Manual: 

ft_strlen

#### Overview
The ft_strlen function calculates the length of a given string, excluding the null-terminating character.

#### Function Prototype
```c
size_t ft_strlen(const char *c);
```

#### Parameters
- c: The string whose length is to be calculated.

#### Return Value
- Returns the length of the string as a `size_t` value.

#### Detailed Explanation
The function iterates through each character of the string until it encounters the null-terminating character (`'\0'`). It increments a counter for each character, and finally returns the counter value, which represents the length of the string.

#### Code
```c
#include "libft.h"

size_t	ft_strlen(const char *c)
{
	size_t	i;

	i = 0;
	while (c[i])
		i++;
	return (i);
}
```

#### Usage Example
Here is an example of how to use the ft_strlen function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char *str = "Hello, World!";
	printf("ft_strlen(\"%s\") = %zu\n", str, ft_strlen(str));
	return 0;
}
```

#### Visual Explanation
1. **Input String: "Hello, World!"**
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Check if c[i] is not null (`'\0'`).
     - c[0] is 'H' (not null), increment `i` to 1.
     - c[1] is 'e' (not null), increment `i` to 2.
     - c[2] is 'l' (not null), increment `i` to 3.
     - c[3] is 'l' (not null), increment `i` to 4.
     - c[4] is 'o' (not null), increment `i` to 5.
     - c[5] is ',' (not null), increment `i` to 6.
     - c[6] is ' ' (not null), increment `i` to 7.
     - c[7] is 'W' (not null), increment `i` to 8.
     - c[8] is 'o' (not null), increment `i` to 9.
     - c[9] is 'r' (not null), increment `i` to 10.
     - c[10] is 'l' (not null), increment `i` to 11.
     - c[11] is 'd' (not null), increment `i` to 12.
     - c[12] is '!' (not null), increment `i` to 13.
     - c[13] is `'\0'` (null), stop the loop.
   - **Step 3**: Return the value of `i`, which is 13.

#### Situations Where ft_strlen is Useful
- **String Manipulation**: Determining the length of a string for operations like copying, concatenation, or formatting.
- **Input Validation**: Checking the length of user input to ensure it meets certain criteria.
- **Buffer Allocation**: Allocating memory for buffers based on the length of a string.
- **Text Processing**: Analyzing and processing text data where the length of strings is important.