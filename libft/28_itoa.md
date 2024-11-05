### Function Manual: 

ft_itoa

#### Overview
The ft_itoa function converts an integer to its corresponding string representation.

#### Function Prototype
```c
char *ft_itoa(int n);
```

#### Parameters
- n: The integer to be converted to a string.

#### Return Value
- Returns a pointer to the newly allocated string representing the integer.
- Returns `NULL` if the allocation fails.

#### Detailed Explanation
The function performs the following steps:
1. **Determine Length**: Calculates the length of the string needed to represent the integer, including space for the sign and null terminator.
2. **Allocate Memory**: Allocates memory for the string.
3. **Handle Special Case**: If the integer is zero, sets the string to "0".
4. **Convert Integer to String**: Converts the integer to a string by extracting each digit and placing it in the string.
5. **Add Null Terminator**: Adds a null terminator at the end of the string.
6. **Return Result**: Returns the newly allocated string.

#### Code
```c
#include "libft.h"

static int	int_len(long nbr);
static char	*pre_conv(int len);

static char	*pre_conv(int len)
{
	char	*tmp;
	tmp = malloc((len + 1) * sizeof(char));
	if (!tmp)
		return (NULL);
	tmp[len] = '\0';
	return (tmp);
}

static int	int_len(long nbr)
{
	int	count;
	count = 0;
	if (nbr < 0)
	{
		count++;
		nbr = -nbr;
	}
	if (nbr == 0)
		count++;
	while (nbr != 0)
	{
		nbr /= 10;
		count++;
	}
	return (count);
}

char	*ft_itoa(int n)
{
	int		len;
	int		i;
	char	*result;
	long	nbr;
	nbr = n;
	len = int_len(nbr);
	result = pre_conv(len);
	if (!result)
		return (NULL);
	i = len - 1;
	if (nbr < 0)
	{
		result[0] = '-';
		nbr = -nbr;
	}
	if (nbr == 0)
		result[i--] = '0';
	while (nbr > 0)
	{
		result[i--] = (nbr % 10) + '0';
		nbr /= 10;
	}
	return (result);
}
```

#### Usage Example
Here is an example of how to use the ft_itoa function:
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <limits.h>
#include "libft.h"

void test_ft_itoa(int n, const char *expected)
{
	char *result = ft_itoa(n);
	if (strcmp(result, expected) == 0)
		printf("Test passed for input %d\n", n);
	else {
		printf("Test failed for input %d\n", n);
		printf("Expected = \"%s\"\n", expected);
		printf("Got \"%s\"\n", result);
	}
	free(result);
}

int main()
{
	test_ft_itoa(0, "0");
	test_ft_itoa(123, "123");
	test_ft_itoa(-123, "-123");
	test_ft_itoa(INT_MAX, "2147483647");
	test_ft_itoa(INT_MIN, "-2147483648");
	return 0;
}
```

### Visual Explanation

#### Input Integer: 123
1. **Determine Length**
   - Calculate the length of the string needed to represent 123.
   - Length is 3.
2. **Allocate Memory**
   - Allocate memory for a string of length 4 (3 digits + null terminator).
3. **Convert Integer to String**
   - Extract each digit from the integer and place it in the string.
     - '3' -> result[2]
     - '2' -> result[1]
     - '1' -> result[0]
4. **Add Null Terminator**
   - result[3] = '\0'
5. **Return Result**
   - Return the string "123".

#### Input Integer: -456
1. **Determine Length**
   - Calculate the length of the string needed to represent -456.
   - Length is 4 (3 digits + sign).
2. **Allocate Memory**
   - Allocate memory for a string of length 5 (4 characters + null terminator).
3. **Convert Integer to String**
   - Extract each digit from the integer and place it in the string.
     - '6' -> result[3]
     - '5' -> result[2]
     - '4' -> result[1]
     - '-' -> result[0]
4. **Add Null Terminator**
   - result[4] = '\0'
5. **Return Result**
   - Return the string "-456".

#### Input Integer: INT_MAX (2147483647)
1. **Determine Length**
   - Calculate the length of the string needed to represent 2147483647.
   - Length is 10.
2. **Allocate Memory**
   - Allocate memory for a string of length 11 (10 digits + null terminator).
3. **Convert Integer to String**
   - Extract each digit from the integer and place it in the string.
     - '7' -> result[9]
     - '4' -> result[8]
     - '6' -> result[7]
     - '3' -> result[6]
     - '8' -> result[5]
     - '4' -> result[4]
     - '7' -> result[3]
     - '4' -> result[2]
     - '1' -> result[1]
     - '2' -> result[0]
4. **Add Null Terminator**
   - result[10] = '\0'
5. **Return Result**
   - Return the string "2147483647".

#### Input Integer: INT_MIN (-2147483648)
1. **Determine Length**
   - Calculate the length of the string needed to represent -2147483648.
   - Length is 11 (10 digits + sign).
2. **Allocate Memory**
   - Allocate memory for a string of length 12 (11 characters + null terminator).
3. **Convert Integer to String**
   - Extract each digit from the integer and place it in the string.
     - '8' -> result[10]
     - '4' -> result[9]
     - '6' -> result[8]
     - '3' -> result[7]
     - '8' -> result[6]
     - '4' -> result[5]
     - '7' -> result[4]
     - '4' -> result[3]
     - '1' -> result[2]
     - '2' -> result[1]
     - '-' -> result[0]
4. **Add Null Terminator**
   - result[11] = '\0'
5. **Return Result**
   - Return the string "-2147483648".

#### Situations Where ft_itoa is Useful
- **Data Conversion**: Converting integers to strings for display or further processing.
- **Logging**: Creating string representations of integers for logging purposes.
- **User Input**: Converting numeric input from users to strings for validation or storage.
- **Configuration**: Generating string representations of configuration values for display or storage.