### Function Manual: 

ft_strlcat

#### Overview
The ft_strlcat function appends the src string to the dst string, ensuring that the result is null-terminated and does not exceed dstsize bytes.

#### Function Prototype
```c
size_t ft_strlcat(char *dst, const char *src, size_t dstsize);
```

#### Parameters
- dst: The destination buffer where the string will be appended.
- src: The source string to be appended.
- dstsize: The size of the destination buffer.

#### Return Value
- Returns the total length of the string it tried to create, which is the initial length of dst plus the length of src.

#### Detailed Explanation
The function first calculates the lengths of the dst and src
 strings. If dstsize is less than or equal to the length of dst, it returns the length of src plus dstsize. Otherwise, it appends characters from src to dst until dstsize - 1 is reached, ensuring the result is null-terminated.

#### Code
```c
#include "libft.h"

size_t	ft_strlcat(char *dst, const char *src, size_t dstsize)
{
	size_t	i;
	size_t	dst_len;
	size_t	src_len;

	i = 0;
	dst_len = ft_strlen(dst);
	src_len = ft_strlen(src);
	if (dstsize <= dst_len)
		return (src_len + dstsize);
	while (src[i] && (dst_len + i) < dstsize - 1)
	{
		dst[dst_len + i] = src[i];
		i++;
	}
	dst[dst_len + i] = '\0';
	return (dst_len + src_len);
}
```

#### Usage Example
Here is an example of how to use the ft_strlcat function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char dst[20] = "Hello, ";
	const char *src = "World!";
	size_t dstsize = sizeof(dst);

	size_t result = ft_strlcat(dst, src, dstsize);
	printf("Resulting string: %s\n", dst);
	printf("Total length: %zu\n", result);

	return 0;
}
```

#### Visual Explanation
1. **Input Parameters**:
   - dst: "Hello, "
   - src: "World!"
   - dstsize: 20

2. **Step-by-Step Process**:
   - **Step 1**: Calculate the lengths of dst and src.
     - `dst_len` is 7.
     - `src_len` is 6.
   - **Step 2**: Check if dstsize is less than or equal to `dst_len`.
     - dstsize is 20, which is greater than `dst_len`.
   - **Step 3**: Append characters from src to dst until dstsize - 1 is reached.
     - Append 'W' to dst[7]
     - Append 'o' to dst[8]
     - Append 'r' to dst[9]
     - Append 'l' to dst[10]
     - Append 'd' to dst[11]
     - Append '!' to dst[12]
   - **Step 4**: Null-terminate dst.
     - dst[13] is set to '\0'.
   - **Step 5**: Return the total length of the string it tried to create.
     - Return value is 13.

3. **Final Memory Areas**:
   - dst: "Hello, World!"
   - src: "World!"

#### Situations Where ft_strlcat is Useful
- **String Concatenation**: When you need to concatenate two strings with a known buffer size, ensuring the result is null-terminated.
- **Buffer Management**: Managing buffers in low-level programming, such as appending data to buffers.
- **Safe String Operations**: Preventing buffer overflows by ensuring the destination buffer is not overrun.
- **Text Processing**: Concatenating and manipulating strings in text processing applications.
