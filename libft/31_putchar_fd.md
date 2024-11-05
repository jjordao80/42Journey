### Function Manual: 

ft_putchar_fd

#### Overview
The ft_putchar_fd function writes a single character to the specified file descriptor.

#### Function Prototype
```c
void ft_putchar_fd(char c, int fd);
```

#### Parameters
- c: The character to be written.
- fd: The file descriptor to which the character will be written.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Include Header**: Includes the necessary header file libft.h which contains the function prototype and any required dependencies.
2. **Function Definition**: Defines the function ft_putchar_fd with parameters c (character to write) and fd (file descriptor).
3. **Write Character**: Uses the `write` system call to write the character c to the file descriptor fd.

#### Code
```c
#include "libft.h"

void	ft_putchar_fd(char c, int fd)
{
	write(fd, &c, 1);
}
```

#### Usage Example
Here is an example of how to use the ft_putchar_fd function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
	char c = 'A';
	int fd = 1; // Standard output
	ft_putchar_fd(c, fd);
	return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - Character to write: 'A'
   - File descriptor: 1 (standard output)
2. **Function Call**: ft_putchar_fd('A', 1)
3. **Step-by-Step Execution**:
   - **Step 1**: Include the header file libft.h.
   - **Step 2**: Define the function ft_putchar_fd with parameters c and fd.
   - **Step 3**: Call the `write` system call with the file descriptor fd, the address of the character `&c`, and the number of bytes to write `1`.
   - **Step 4**: The character 'A' is written to the standard output.

#### Additional Examples

1. **Writing to a File**:
```c
#include <stdio.h>
#include <fcntl.h>
#include "libft.h"

int main(void)
{
	char c = 'B';
	int fd = open("output.txt", O_WRONLY | O_CREAT, 0644);
	if (fd == -1)
	{
		perror("Error opening file");
		return 1;
	}
	ft_putchar_fd(c, fd);
	close(fd);
	return 0;
}
```
**Visual Explanation**:
- **Initial Setup**:
  - Character to write: 'B'
  - File descriptor: File opened for writing (`output.txt`)
- **Function Call**: ft_putchar_fd('B', fd)
- **Step-by-Step Execution**:
  - **Step 1**: Include the header file libft.h.
  - **Step 2**: Open the file `output.txt` for writing.
  - **Step 3**: Define the function ft_putchar_fd with parameters c and fd.
  - **Step 4**: Call the `write` system call with the file descriptor fd, the address of the character `&c`, and the number of bytes to write `1`.
  - **Step 5**: The character 'B' is written to the file `output.txt`.
  - **Step 6**: Close the file descriptor.

2. **Writing to Standard Error**:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
	char c = 'C';
	int fd = 2; // Standard error
	ft_putchar_fd(c, fd);
	return 0;
}
```
**Visual Explanation**:
- **Initial Setup**:
  - Character to write: 'C'
  - File descriptor: 2 (standard error)
- **Function Call**: ft_putchar_fd('C', 2)
- **Step-by-Step Execution**:
  - **Step 1**: Include the header file libft.h.
  - **Step 2**: Define the function ft_putchar_fd with parameters c and fd.
  - **Step 3**: Call the `write` system call with the file descriptor fd, the address of the character `&c`, and the number of bytes to write `1`.
  - **Step 4**: The character 'C' is written to the standard error.

#### Situations Where ft_putchar_fd is Useful
- **Output to Files**: Writing characters to files or other file descriptors.
- **Logging**: Writing log messages to a log file or standard error.
- **Terminal Output**: Displaying characters on the terminal or console.
- **Custom Output Streams**: Writing characters to custom output streams, such as network sockets or pipes.