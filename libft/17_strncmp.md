### Function Manual:

ft_strncmp

#### Overview
The ft_strncmp function compares up to n characters of two strings s1 and s2.

#### Function Prototype
```c
int ft_strncmp(const char *s1, const char *s2, size_t n);
```

#### Parameters
- s1: The first string to be compared.
- s2: The second string to be compared.
- n: The maximum number of characters to compare.

#### Return Value
- Returns `0` if the first n characters of s1 and s2 are equal.
- Returns a positive value if the first differing character in s1 is greater than the corresponding character in s2.
- Returns a negative value if the first differing character in s1 is less than the corresponding character in s2.

#### Detailed Explanation
The function compares the characters of s1 and s2 up to n characters or until a null-terminating character is encountered. It returns the difference between the first differing characters as unsigned characters.

#### Code
```c
#include "libft.h"

int	ft_strncmp(const char *s1, const char *s2, size_t n)
{
	unsigned int	i;

	i = 0;
	if (n == 0)
	{
		return (0);
	}
	while (i < n && s1[i] == s2[i] && s1[i] != '\0' && s2[i] != '\0')
	{
		i++;
	}
	if (i == n)
	{
		return (0);
	}
	return ((unsigned char)s1[i] - (unsigned char)s2[i]);
}
```

#### Usage Example
Here is an example of how to use the ft_strncmp function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
    char *str1 = "Hello, World!";
    char *str2 = "Hello, 42!";
    size_t n = 5;

    int result = ft_strncmp(str1, str2, n);
    printf("ft_strncmp(\"%s\", \"%s\", %zu) = %d\n", str1, str2, n, result);

    return 0;
}
```

Let's complete the visual explanation for the `ft_strncmp` function.

### Visual Explanation
1. **Input Strings: "Hello, World!" and "Hello, 42!"**
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Check if `n` is 0.
     - If `n` is 0, return 0.
   - **Step 3**: Compare characters of `s1` and `s2` while `i` is less than `n`, `s1[i]` is equal to `s2[i]`, and neither `s1[i]` nor `s2[i]` is null.
     - `s1[0]` is 'H' and `s2[0]` is 'H' (equal), increment `i` to 1.
     - `s1[1]` is 'e' and `s2[1]` is 'e' (equal), increment `i` to 2.
     - `s1[2]` is 'l' and `s2[2]` is 'l' (equal), increment `i` to 3.
     - `s1[3]` is 'l' and `s2[3]` is 'l' (equal), increment `i` to 4.
     - `s1[4]` is 'o' and `s2[4]` is 'o' (equal), increment `i` to 5.
   - **Step 4**: If `i` equals `n`, return 0.
   - **Step 5**: Return the difference between `s1[i]` and `s2[i]` as unsigned characters.
     - Since `i` equals `n` (5), the loop terminates and the function returns 0.

2. **Input Strings: "Hello, World!" and "Hello, 42!" with `n` = 7**
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Check if `n` is 0.
     - If `n` is 0, return 0.
   - **Step 3**: Compare characters of `s1` and `s2` while `i` is less than `n`, `s1[i]` is equal to `s2[i]`, and neither `s1[i]` nor `s2[i]` is null.
     - `s1[0]` is 'H' and `s2[0]` is 'H' (equal), increment `i` to 1.
     - `s1[1]` is 'e' and `s2[1]` is 'e' (equal), increment `i` to 2.
     - `s1[2]` is 'l' and `s2[2]` is 'l' (equal), increment `i` to 3.
     - `s1[3]` is 'l' and `s2[3]` is 'l' (equal), increment `i` to 4.
     - `s1[4]` is 'o' and `s2[4]` is 'o' (equal), increment `i` to 5.
     - `s1[5]` is ',' and `s2[5]` is ',' (equal), increment `i` to 6.
     - `s1[6]` is ' ' and `s2[6]` is ' ' (equal), increment `i` to 7.
   - **Step 4**: If `i` equals `n`, return 0.
   - **Step 5**: Return the difference between `s1[i]` and `s2[i]` as unsigned characters.
     - Since `i` equals `n` (7), the loop terminates and the function returns 0.

3. **Input Strings: "Hello, World!" and "Hello, 42!" with `n` = 10**
   - **Step 1**: Initialize `i` to 0.
   - **Step 2**: Check if `n` is 0.
     - If `n` is 0, return 0.
   - **Step 3**: Compare characters of `s1` and `s2` while `i` is less than `n`, `s1[i]` is equal to `s2[i]`, and neither `s1[i]` nor `s2[i]` is null.
     - `s1[0]` is 'H' and `s2[0]` is 'H' (equal), increment `i` to 1.
     - `s1[1]` is 'e' and `s2[1]` is 'e' (equal), increment `i` to 2.
     - `s1[2]` is 'l' and `s2[2]` is 'l' (equal), increment `i` to 3.
     - `s1[3]` is 'l' and `s2[3]` is 'l' (equal), increment `i` to 4.
     - `s1[4]` is 'o' and `s2[4]` is 'o' (equal), increment `i` to 5.
     - `s1[5]` is ',' and `s2[5]` is ',' (equal), increment `i` to 6.
     - `s1[6]` is ' ' and `s2[6]` is ' ' (equal), increment `i` to 7.
     - `s1[7]` is 'W' and `s2[7]` is '4' (not equal), exit loop.
   - **Step 4**: If `i` equals `n`, return 0.
   - **Step 5**: Return the difference between `s1[i]` and `s2[i]` as unsigned characters.
     - `s1[7]` is 'W' (87 in ASCII) and `s2[7]` is '4' (52 in ASCII), so the function returns 87 - 52 = 35.

#### Situations Where ft_strncmp is Useful
- **String Comparison**: Comparing prefixes of strings up to a specified length.
- **Sorting**: Implementing custom sorting algorithms that require string comparison.
- **Input Validation**: Checking if user input matches a specific pattern or prefix.
- **Text Processing**: Comparing parts of strings in text processing applications.
