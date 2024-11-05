### Function Manual: 

ft_memmove

#### Overview
The ft_memmove function copies n bytes from memory area src to memory area dst. The memory areas may overlap.

#### Function Prototype
```c
void *ft_memmove(void *dst, const void *src, size_t n);
```

#### Parameters
- dst: A pointer to the destination memory area.
- src: A pointer to the source memory area.
- n: The number of bytes to copy.

#### Return Value
- Returns a pointer to the destination memory area dst.

#### Detailed Explanation
The function handles overlapping memory areas by checking the relative positions of dst and src. If dst is before src, it copies the bytes from the beginning. If dst is after src, it copies the bytes from the end to avoid overwriting the source data.

#### Code
```c
#include "libft.h"

void *ft_memmove(void *dst, const void *src, size_t n)
{
    size_t i;

    if (!dst && !src)
        return (NULL);
    if (dst < src)
    {
        i = 0;
        while (i < n)
        {
            ((char *)dst)[i] = ((char *)src)[i];
            i++;
        }
    }
    else
    {
        i = n;
        while (i > 0)
        {
            ((char *)dst)[i - 1] = ((char *)src)[i - 1];
            i--;
        }
    }
    return (dst);
}
```

#### Usage Example
Here is an example of how to use the ft_memmove function:
```c
#include <stdio.h>
#include <string.h>
#include "libft.h"

int main()
{
    char src1[] = "Hello, World!";
    char dst1[50];
    char src2[] = "Hello, World!";
    char dst2[50];

    // Test without overlapping
    ft_memmove(dst1, src1, strlen(src1) + 1);
    memmove(dst2, src1, strlen(src1) + 1);
    printf("ft_memmove without overlap: %s\n", dst1);
    printf("memmove without overlap: %s\n", dst2);

    // Test with overlapping
    ft_memmove(src1 + 5, src1, strlen(src1) + 1);
    memmove(src2 + 5, src2, strlen(src2) + 1);
    printf("ft_memmove with overlap: %s\n", src1);
    printf("memmove with overlap: %s\n", src2);

    return 0;
}
```

#### Visual Explanation
1. **Input Memory Areas**:
   - src: "Hello, World!"
   - dst: Uninitialized memory area.
   - n: 13 (number of bytes to copy).

2. **Step-by-Step Process**:
   - **Step 1**: Check if dst and src are `NULL`.
     - If both are `NULL`, return `NULL`.
   - **Step 2**: Check if dst is less than src.
     - If dst is less than src, copy from the beginning.
     - Initialize `i` to 0.
     - Copy each byte from src to dst until `i` reaches n.
   - **Step 3**: If dst is greater than or equal to src, copy from the end.
     - Initialize `i` to n.
     - Copy each byte from src to dst in reverse order until `i` reaches 0.
   - **Step 4**: Return the pointer to the destination memory area dst.

3. **Final Memory Areas**:
   - src: "Hello, World!"
   - dst: "Hello, World!"

#### Situations Where ft_memmove is Useful
- **Copying Data**: When you need to copy a block of memory from one location to another, especially when the memory areas overlap.
- **Buffer Management**: Managing buffers in low-level programming, such as copying data to and from buffers.
- **Data Serialization**: Copying data structures to a contiguous block of memory for serialization.
- **Performance Optimization**: Using efficient memory copying for performance-critical applications.
