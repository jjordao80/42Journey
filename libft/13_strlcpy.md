### Function Manual: 

ft_strlcpy

#### Overview
The ft_strlcpy function copies up to dstsize - 1 characters from the string src to dst, null-terminating the result if dstsize is not 0.

#### Function Prototype
```c
size_t ft_strlcpy(char *dst, const char *src, size_t dstsize);
```

#### Parameters
- dst: The destination buffer where the string will be copied.
- src: The source string to be copied.
- dstsize: The size of the destination buffer.

#### Return Value
- Returns the total length of the string it tried to create, which is the length of src.

#### Detailed Explanation
The function first calculates the length of the source string src. If dstsize is 0, it returns the length of src without copying anything. Otherwise, it copies up to dstsize - 1 characters from src to dst and null-terminates dst.

#### Code
```c
#include "libft.h"

size_t	ft_strlcpy(char *dst, const char *src, size_t dstsize)
{
	size_t	i;
	size_t	src_len;

	i = 0;
	src_len = 0;
	while (src[src_len])
		src_len++;
	if (dstsize == 0)
		return (src_len);
	while (src[i] && i < dstsize - 1)
	{
		dst[i] = src[i];
		i++;
	}
	dst[i] = '\0';
	return (src_len);
}
```

#### Usage Example
Here is an example of how to use the ft_strlcpy function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char src[] = "Hello, World!";
	char dst[20];
	size_t result;

	result = ft_strlcpy(dst, src, sizeof(dst));
	printf("Copied string: %s\n", dst);
	printf("Length of source string: %zu\n", result);

	return 0;
}
```

#### Visual Explanation
1. **Input Parameters**:
   - src: "Hello, World!"
   - dst: Uninitialized buffer
   - dstsize: 20

2. **Step-by-Step Process**:
   - **Step 1**: Calculate the length of src.
     - `src_len` is 13.
   - **Step 2**: Check if dstsize is 0.
     - dstsize is 20, so continue.
   - **Step 3**: Copy characters from src to dst up to dstsize - 1.
     - Copy 'H' to dst[0]
     - Copy 'e' to dst[1]
     - Copy 'l' to dst[2]
     - Copy 'l' to dst[3]
     - Copy 'o' to dst[4]
     - Copy ',' to dst[5]
     - Copy ' ' to dst[6]
     - Copy 'W' to dst[7]
     - Copy 'o' to dst[8]
     - Copy 'r' to dst[9]
     - Copy 'l' to dst[10]
     - Copy 'd' to dst[11]
     - Copy '!' to dst[12]
   - **Step 4**: Null-terminate dst.
     - dst[13] is set to '\0'.
   - **Step 5**: Return the length of src.
     - Return value is 13.

3. **Final Memory Areas**:
   - src: "Hello, World!"
   - dst: "Hello, World!"

#### Situations Where ft_strlcpy is Useful
- **String Copying**: When you need to copy a string to a buffer with a known size, ensuring it is null-terminated.
- **Buffer Management**: Managing buffers in low-level programming, such as copying data to and from buffers.
- **Safe String Operations**: Preventing buffer overflows by ensuring the destination buffer is not overrun.
- **Text Processing**: Copying and manipulating strings in text processing applications.
