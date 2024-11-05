### Function Manual: 

ft_memcpy

#### Overview
The ft_memcpy function copies n bytes from memory area src to memory area dst.

#### Function Prototype
```c
void *ft_memcpy(void *dst, const void *src, size_t n);
```

#### Parameters
- dst: A pointer to the destination memory area.
- src: A pointer to the source memory area.
- n: The number of bytes to copy.

#### Return Value
- Returns a pointer to the destination memory area dst.

#### Detailed Explanation
The function iterates through the memory areas pointed to by src
 and dst, copying each byte from src to dst until n bytes have been copied.

#### Code
```c
#include "libft.h"

void *ft_memcpy(void *dst, const void *src, size_t n)
{
    size_t i;

    i = 0;
    while (i < n)
    {
        ((unsigned char *)dst)[i] = ((unsigned char *)src)[i];
        i++;
    }
    return (dst);
}
```

#### Usage Example
Here is an example of how to use the ft_memcpy function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    char src[50] = "This is the source string.";
    char dst[50];
    char dst2[50];

    // Using ft_memcpy
    ft_memcpy(dst, src, 23);
    dst[23] = '\0'; // Null-terminate for printing

    // Using memcpy
    memcpy(dst2, src, 23);
    dst2[23] = '\0'; // Null-terminate for printing

    // Display results
    printf("Using ft_memcpy: %s\n", dst);
    printf("Using memcpy:    %s\n", dst2);

    return 0;
}
```
#### Visual Explanation
1. **Input Memory Areas**:
   - src: "This is the source string."
   - dst: Uninitialized memory area.
   - n: 23 (number of bytes to copy).

2. **Step-by-Step Process**:
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Copy the byte from src[i] to dst[i].
     - src[0] ('T') -> dst[0] ('T')
     - src[1] ('h') -> dst[1] ('h')
     - src[2] ('i') -> dst[2] ('i')
     - Continue this process until `i` reaches 23.
   - **Step 3**: Increment `i` and repeat Step 2 until `i` equals n.
   - **Step 4**: Return the pointer to the destination memory area dst.

3. **Final Memory Areas**:
   - src: "This is the source string."
   - dst: "This is the source strin"

#### Situations Where 

ft_memcpy is Useful
- **Copying Data**: When you need to copy a block of memory from one location to another.
- **Buffer Management**: Managing buffers in low-level programming, such as copying data to and from buffers.
- **Data Serialization**: Copying data structures to a contiguous block of memory for serialization.
- **Performance Optimization**: Using efficient memory copying for performance-critical applications.
