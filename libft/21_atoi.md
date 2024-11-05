### Function Manual: 

ft_atoi

#### Overview
The ft_atoi function converts a string representation of an integer to its corresponding integer value.

#### Function Prototype
```c
int ft_atoi(const char *str);
```
#### Parameters
- str: The string to be converted to an integer.

#### Return Value
- Returns the integer value represented by the string.

#### Detailed Explanation
The function processes the input string str to convert it to an integer:
1. It skips any leading whitespace characters.
2. It checks for an optional sign (`+` or `-`).
3. It iterates through the numeric characters, converting them to an integer.

#### Code
```c
#include "libft.h"

int	ft_atoi(const char *str)
{
	int	i;
	int	r;
	int	s;

	i = 0;
	s = 1;
	r = 0;
	while (str[i] == 32 || (str[i] >= 9 && str[i] <= 13))
		i++;
	if (str[i] == '+' && str[i + 1] != '-')
		i++;
	if (str[i] == '-')
	{
		s = -1;
		i++;
	}
	while (str[i] >= '0' && str[i] <= '9')
	{
		r *= 10;
		r += str[i] - '0';
		i++;
	}
	return (r *= s);
}
```

#### Usage Example
Here is an example of how to use the ft_atoi function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
    char *str = "  -12345";
    int result = ft_atoi(str);
    printf("The integer value is: %d\n", result);
    return 0;
}
```

#### Visual Explanation
1. **Input String: "  -12345"**
   - **Step 1**: Initialize variables `i` to 0, `s` to 1, and `r` to 0.
   - **Step 2**: Skip leading whitespace characters.
     - str[0] is a space, increment `i` to 1.
     - str[1] is a space, increment `i` to 2.
   - **Step 3**: Check for an optional sign.
     - str[2] is '-', set `s` to -1 and increment `i` to 3.
   - **Step 4**: Convert numeric characters to an integer.
     - str[3] is '1', update `r` to 1 and increment `i` to 4.
     - str[4] is '2', update `r` to 12 and increment `i` to 5.
     - str[5] is '3', update `r` to 123 and increment `i` to 6.
     - str[6] is '4', update `r` to 1234 and increment `i` to 7.
     - str[7] is '5', update `r` to 12345 and increment `i` to 8.
   - **Step 5**: Apply the sign to the result.
     - `r` is 12345, multiply by `s` (-1) to get -12345.
   - **Step 6**: Return the result.
     - The function returns -12345.

#### Situations Where ft_atoi is Useful
- **Input Parsing**: Converting numeric input from strings to integers.
- **Configuration Reading**: Reading and converting numeric configuration values from text files.
- **Data Processing**: Converting numeric data in string format to integers for calculations.
- **Command-Line Arguments**: Parsing numeric command-line arguments.