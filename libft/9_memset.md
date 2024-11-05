### Function Manual: 

ft_memset

#### Overview
The ft_memset function fills the first len bytes of the memory area pointed to by b with the constant byte c.

#### Function Prototype
```c
void *ft_memset(void *b, int c, size_t len);
```

#### Parameters
- b: A pointer to the memory area to be filled.
- c: The byte value to be set. It is passed as an `int` but is converted to an `unsigned char`.
- len: The number of bytes to be set to the value.

#### Return Value
- Returns a pointer to the memory area b.

#### Detailed Explanation
The function iterates through the memory area pointed to by b and sets each byte to the value of c until len bytes have been set.

#### Code
```c
#include "libft.h"

void *ft_memset(void *b, int c, size_t len)
{
    unsigned char *tmp_var;

    tmp_var = (unsigned char *) b;
    while (len > 0)
    {
        *(tmp_var++) = (unsigned char) c;
        len--;
    }
    return (b);
}
```

#### Usage Example
Here is an example of how to use the ft_memset function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    char str[] = "Hello, World!";
    int c = 'a';
    size_t len = 6;

    printf("Before memset: %s\n", str);
    ft_memset(str, c, len);
    printf("After memset: %s\n", str);
    return 0;
}
```

#### Visual Explanation
1. **Input String: "Hello, World!"**
   - **Step 1**: Initialize `tmp_var` to point to the start of the memory area b
   - **Step 2**: Set the first byte to c ('a').
     - Memory: `aello, World!`
   - **Step 3**: Move `tmp_var` to the next byte and decrement len
   - **Step 4**: Repeat steps 2 and 3 until len bytes have been set.
     - Memory: `aaaaaa, World!`
   - **Step 5**: Return the pointer to the memory area b

#### Situations Where ft_memset is Useful
- **Initializing Memory**: Setting all bytes of a memory block to a specific value, such as zeroing out memory.
- **Buffer Preparation**: Preparing a buffer with a specific pattern before use.
- **Clearing Sensitive Data**: Overwriting sensitive data in memory before freeing it to prevent data leaks.
- **Custom Memory Patterns**: Creating custom memory patterns for testing or other purposes.