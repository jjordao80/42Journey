### Function Manual: 

ft_split

#### Overview
The ft_split function splits a string into an array of substrings based on a specified delimiter character.

#### Function Prototype
```c
char **ft_split(char const *s, char c);
```

#### Parameters
- s: The original string to be split.
- c: The delimiter character used to split the string.

#### Return Value
- Returns a pointer to an array of strings (substrings).
- Returns `NULL` if the allocation fails or if the input string s is `NULL`.

#### Detailed Explanation
The function performs the following steps:
1. **Count Words**: Counts the number of words in the string s separated by the delimiter c.
2. **Allocate Memory**: Allocates memory for the array of strings.
3. **Split String**: Iterates through the string s and extracts each word, storing it in the array.
4. **Null-Terminate Array**: Adds a `NULL` pointer at the end of the array to mark the end.

#### Code
```c
#include "libft.h"

static int	ft_count_words(char const *s, char c)
{
	int	words;
	int	i;

	words = 0;
	i = 0;
	while (s[i])
	{
		if (s[i] != c)
		{
			words++;
			while (s[i] && s[i] != c)
				i++;
		}
		else
			i++;
	}
	return (words);
}

static char	*ft_get_word(char const *s, char c, int *i)
{
	int		j;
	char	*word;

	j = 0;
	while (s[*i + j] && s[*i + j] != c)
		j++;
	word = (char *)malloc(sizeof(char) * (j + 1));
	if (!word)
		return (NULL);
	j = 0;
	while (s[*i] && s[*i] != c)
		word[j++] = s[(*i)++];
	word[j] = '\0';
	return (word);
}

char	**ft_split(char const *s, char c)
{
	char	**split;
	int		i;
	int		j;

	if (!s)
		return (NULL);
	split = (char **)malloc(sizeof(char *) * (ft_count_words(s, c) + 1));
	if (!split)
		return (NULL);
	i = 0;
	j = 0;
	while (s[i])
	{
		if (s[i] != c)
		{
			split[j] = ft_get_word(s, c, &i);
			if (!split[j])
				return (NULL);
			j++;
		}
		else
			i++;
	}
	split[j] = NULL;
	return (split);
}
```

#### Usage Example
Here is an example of how to use the ft_split function:
```c
#include <stdio.h>
#include "libft.h"

int main()
{
	char *s = "Arroz outra vez";
	char **result = ft_split(s, ' ');
	
	for (int i = 0; result[i]; i++)
	{
		printf("result[%d] = \"%s\"\n", i, result[i]);
	}
	return 0;
}
```

### Visual Explanation

1. **Input String: "Arroz outra vez"**
   - **Step 1**: Count the number of words separated by the delimiter ' '.
     - Initialize `words` to 0.
     - Iterate through the string:
       - 'A' is not ' ', increment `words` to 1.
       - 'r' is not ' ', continue.
       - 'r' is not ' ', continue.
       - 'o' is not ' ', continue.
       - 'z' is not ' ', continue.
       - ' ' is ' ', stop counting this word.
       - 'o' is not ' ', increment `words` to 2.
       - 'u' is not ' ', continue.
       - 't' is not ' ', continue.
       - 'r' is not ' ', continue.
       - 'a' is not ' ', continue.
       - ' ' is ' ', stop counting this word.
       - 'v' is not ' ', increment `words` to 3.
       - 'e' is not ' ', continue.
       - 'z' is not ' ', continue.
     - Total words: 3 ("Arroz", "outra", "vez")

   - **Step 2**: Allocate memory for the array of strings.
     - Allocate memory for 4 elements (3 words + 1 `NULL` terminator).
     - Memory: `split` array with 4 elements.

   - **Step 3**: Iterate through the string and extract each word.
     - Initialize `i` to 0 and `j` to 0.
     - Iterate through the string:
       - 'A' is not ' ', start extracting the word:
         - Extract 'A', 'r', 'r', 'o', 'z'.
         - Store "Arroz" in `split[0]`.
         - Increment `j` to 1.
       - ' ' is ' ', skip.
       - 'o' is not ' ', start extracting the word:
         - Extract 'o', 'u', 't', 'r', 'a'.
         - Store "outra" in `split[1]`.
         - Increment `j` to 2.
       - ' ' is ' ', skip.
       - 'v' is not ' ', start extracting the word:
         - Extract 'v', 'e', 'z'.
         - Store "vez" in `split[2]`.
         - Increment `j` to 3.

   - **Step 4**: Null-terminate the array.
     - Set `split[3]` to `NULL`.

2. **Final Memory Areas**:
   - `split[0]`: "Arroz"
   - `split[1]`: "outra"
   - `split[2]`: "vez"
   - `split[3]`: `NULL`

#### Situations Where ft_split is Useful
- **String Tokenization**: Splitting a string into tokens based on a delimiter for parsing or processing.
- **Data Parsing**: Extracting individual elements from a delimited string, such as CSV data.
- **Text Processing**: Breaking down text into words or phrases for analysis or manipulation.
- **Command-Line Arguments**: Parsing command-line arguments or input strings into separate components.