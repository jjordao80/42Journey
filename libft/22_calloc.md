### Function Manual: 

ft_calloc

#### Overview
The ft_calloc function allocates memory for an array of number elements, each of size bytes, and initializes all bytes in the allocated memory to zero.

#### Function Prototype
```c
void *ft_calloc(size_t number, size_t size);
```

#### Parameters
- number: The number of elements to allocate.
- size: The size of each element in bytes.

#### Return Value
- Returns a pointer to the allocated memory.
- Returns `NULL` if the allocation fails.

#### Detailed Explanation
The function performs the following steps:
1. **Memory Allocation**: Allocates memory for number elements, each of size bytes, using `malloc`.
2. **Null Check**: Checks if the allocation was successful. If not, returns `NULL`.
3. **Memory Initialization**: Uses ft_bzero to set all bytes in the allocated memory to zero.
4. **Return Pointer**: Returns a pointer to the allocated and zero-initialized memory.

#### Code
```c
#include "libft.h"

void	*ft_calloc(size_t number, size_t size)
{
	void	*ptr;

	ptr = malloc(number * size);
	if (!ptr)
		return (NULL);
	ft_bzero(ptr, number * size);
	return (ptr);
}
```

#### Usage Example
Here is an example of how to use the ft_calloc function:
```c
#include <stdio.h>
#include <stdlib.h>
#include "libft.h"

int main()
{
	size_t number = 5;
	size_t size = 10;
	void *result = ft_calloc(number, size);
	if (result)
	{
		printf("Memory allocated and initialized to zero.\n");
		free(result);
	}
	else
	{
		printf("Memory allocation failed.\n");
	}
	return 0;
}
```

#### Visual Explanation
1. **Input Parameters**:
   - number: 5
   - size: 10
2. **Step-by-Step Process**:
   - **Step 1**: Calculate the total size to allocate.
     - `total_size = number * size = 5 * 10 = 50` bytes.
   - **Step 2**: Allocate memory using `malloc`.
     - `ptr = malloc(50)`
     - If `malloc` fails, `ptr` is `NULL`.
   - **Step 3**: Check if the allocation was successful.
     - If `ptr` is `NULL`, return `NULL`.
   - **Step 4**: Initialize the allocated memory to zero using ft_bzero.
     - ft_bzero(ptr, 50)
   - **Step 5**: Return the pointer to the allocated memory.
     - `return ptr`
3. **Final Memory State**:
   - The allocated memory block of 50 bytes is set to zero.

#### Situations Where ft_calloc is Useful
- **Array Allocation**: Allocating memory for an array of elements and initializing it to zero.
- **Buffer Initialization**: Creating a buffer with all bytes set to zero.
- **Dynamic Memory Management**: Managing dynamic memory allocation in programs where zero-initialized memory is required.
- **Data Structures**: Allocating and initializing memory for data structures like arrays, matrices, or linked lists.