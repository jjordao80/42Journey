### Function Manual: 

ft_memcmp

#### Overview
The ft_memcmp function compares the first n bytes of the memory areas s1 and s2.

#### Function Prototype
```c
int ft_memcmp(const void *s1, const void *s2, size_t n);
```

#### Parameters
- s1: A pointer to the first memory area.
- s2: A pointer to the second memory area.
- n: The number of bytes to compare.

#### Return Value
- Returns an integer less than, equal to, or greater than zero if the first n bytes of s1 are found, respectively, to be less than, to match, or be greater than the first n bytes of s2.

#### Detailed Explanation
The function iterates through the memory areas pointed to by s1 and s2, comparing each byte until n bytes have been compared or a difference is found.

#### Code
```c
#include "libft.h"

int	ft_memcmp(const void *s1, const void *s2, size_t n)
{
	size_t	i;

	i = 0;
	while (i < n)
	{
		if (((unsigned char *)s1)[i] != ((unsigned char *)s2)[i])
			return (((unsigned char *)s1)[i] - ((unsigned char *)s2)[i]);
		i++;
	}
	return (0);
}
```

#### Usage Example
Here is an example of how to use the ft_memcmp function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char str1[] = "Hello, World!";
	char str2[] = "Hello, World!";
	char str3[] = "Hello, 42!";

	printf("ft_memcmp(str1, str2, 13) = %d\n", ft_memcmp(str1, str2, 13)); // Should return 0
	printf("ft_memcmp(str1, str3, 13) = %d\n", ft_memcmp(str1, str3, 13)); // Should return a non-zero value

	return 0;
}
```

#### Visual Explanation
1. **Input Memory Areas**:
   - s1: "Hello, World!"
   - s2: "Hello, 42!"
   - n: 13 (number of bytes to compare)

2. **Step-by-Step Process**:
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Compare the byte at s1[i] with s2[i].
     - s1[0] ('H') == s2[0] ('H'), increment `i` to 1.
     - s1[1] ('e') == s2[1] ('e'), increment `i` to 2.
     - s1[2] ('l') == s2[2] ('l'), increment `i` to 3.
     - s1[3] ('l') == s2[3] ('l'), increment `i` to 4.
     - s1[4] ('o') == s2[4] ('o'), increment `i` to 5.
     - s1[5] (',') == s2[5] (','), increment `i` to 6.
     - s1[6] (' ') == s2[6] (' '), increment `i` to 7.
     - s1[7] ('W') != s2[7] ('4'), return the difference between s1[7] and s2[7].
   - **Step 3**: If `i` equals n, return 0.
   - **Step 4**: Return the difference between s1[i] and s2[i] as unsigned characters.

3. **Final Memory Areas**:
   - s1: "Hello, World!"
   - s2: "Hello, 42!"

#### Situations Where ft_memcmp is Useful
- **Memory Comparison**: Comparing blocks of memory to check for equality or differences.
- **Sorting**: Implementing custom sorting algorithms that require memory comparison.
- **Data Validation**: Ensuring that two memory areas contain the same data.
- **Binary Data Processing**: Comparing binary data structures or buffers.