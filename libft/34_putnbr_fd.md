### Function Manual: 

ft_putnbr_fd

#### Overview
The ft_putnbr_fd function writes an integer to the specified file descriptor.

#### Function Prototype
```c
void ft_putnbr_fd(int n, int fd);
```

#### Parameters
- n: The integer to be written.
- fd: The file descriptor to which the integer will be written.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Handle Negative Numbers**: If the integer n is negative, it writes a '-' character to the file descriptor and converts n to its positive equivalent.
2. **Recursive Division**: If the integer n is greater than or equal to 10, it recursively calls itself with n / 10 to handle the higher-order digits.
3. **Write Digit**: It writes the last digit of n to the file descriptor by converting it to its character representation.

#### Code
```c
#include "libft.h"

void	ft_putnbr_fd(int n, int fd)
{
	long	nbr;

	nbr = n;
	if (nbr < 0)
	{
		ft_putchar_fd('-', fd);
		nbr = -nbr;
	}
	if (nbr >= 10)
	{
		ft_putnbr_fd(nbr / 10, fd);
		ft_putchar_fd((nbr % 10) + '0', fd);
	}
	else
		ft_putchar_fd(nbr + '0', fd);
}
```

#### Usage Example
Here is an example of how to use the ft_putnbr_fd function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
	int fd = 1; // Standard output
	ft_putnbr_fd(-12345, fd);
	return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - Integer to write: `-12345`
   - File descriptor: `1` (standard output)

2. **Function Call**: ft_putnbr_fd(-12345, 1)

3. **Step-by-Step Execution**:
   - **Step 1**: Check if n is negative.
     - n is `-12345`, so write `'-'` to fd and convert n to `12345`.
   - **Step 2**: Check if n is greater than or equal to `10`.
     - n is `12345`, so recursively call ft_putnbr_fd(1234, 1).
   - **Step 3**: Repeat Step 2 for `1234`, `123`, `12`, and `1`.
     - Write each digit to fd in reverse order of the recursive calls.
   - **Step 4**: Write the digits to fd:
     - Write `'1'`, `'2'`, `'3'`, `'4'`, `'5'` to fd.

#### Situations Where ft_putnbr_fd is Useful
- **Logging**: Writing integer values to log files or standard output for debugging purposes.
- **Output to Files**: Writing integer values to files or other file descriptors.
- **Terminal Output**: Displaying integer values on the terminal or console.
- **Custom Output Streams**: Writing integer values to custom output streams, such as network sockets or pipes.