### Function Manual: 

ft_putstr_fd

#### Overview
The ft_putstr_fd function writes a string to the specified file descriptor.

#### Function Prototype
```c
void ft_putstr_fd(char *s, int fd);
```

#### Parameters
- s: The string to be written.
- fd: The file descriptor to which the string will be written.

#### Return Value
- This function does not return a value.

#### Detailed Explanation
The function performs the following steps:
1. **Include Header**: Includes the necessary header file libft.h which contains the function prototype and any required dependencies.
2. **Function Definition**: Defines the function ft_putstr_fd with parameters s (string to write) and fd (file descriptor).
3. **Write String**: Uses the `write` system call to write the string s to the file descriptor fd.

#### Code
```c
#include "libft.h"

void	ft_putstr_fd(char *s, int fd)
{
	write(fd, s, ft_strlen(s));
}
```

#### Usage Example
Here is an example of how to use the ft_putstr_fd function:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
	char *s = "Hello, World!";
	int fd = 1; // Standard output
	ft_putstr_fd(s, fd);
	return 0;
}
```

#### Visual Explanation
1. **Initial Setup**:
   - String to write: "Hello, World!"
   - File descriptor: 1 (standard output)
2. **Function Call**: ft_putstr_fd("Hello, World!", 1)
3. **Step-by-Step Execution**:
   - **Step 1**: Include the header file libft.h.
   - **Step 2**: Define the function ft_putstr_fd with parameters s and fd.
   - **Step 3**: Call the `write` system call with the file descriptor fd, the address of the string s, and the length of the string ft_strlen(s).
   - **Step 4**: The string "Hello, World!" is written to the standard output.

#### Additional Examples
1. **Writing to a File**:
```c
#include <stdio.h>
#include <fcntl.h>
#include "libft.h"

int main(void)
{
	char *s = "Hello, File!";
	int fd = open("output.txt", O_WRONLY | O_CREAT, 0644);
	if (fd == -1)
	{
		perror("Error opening file");
		return 1;
	}
	ft_putstr_fd(s, fd);
	close(fd);
	return 0;
}
```
**Output**: The string "Hello, File!" is written to `output.txt`.

2. **Writing to Standard Error**:
```c
#include <stdio.h>
#include "libft.h"

int main(void)
{
	char *s = "Hello, Error!";
	int fd = 2; // Standard error
	ft_putstr_fd(s, fd);
	return 0;
}
```
**Output**: The string "Hello, Error!" is written to the standard error.

3. **Writing to a Network Socket**:
```c
#include <stdio.h>
#include <sys/socket.h>
#include "libft.h"

int main(void)
{
	char *s = "Hello, Network!";
	int sockfd = socket(AF_INET, SOCK_STREAM, 0);
	// Assume sockfd is connected to a server
	ft_putstr_fd(s, sockfd);
	close(sockfd);
	return 0;
}
```
**Output**: The string "Hello, Network!" is sent over the network socket.

#### Situations Where ft_putstr_fd is Useful
- **Output to Files**: Writing strings to files or other file descriptors.
- **Logging**: Writing log messages to a log file or standard error.
- **Terminal Output**: Displaying strings on the terminal or console.
- **Custom Output Streams**: Writing strings to custom output streams, such as network sockets or pipes.