### Function Manual: Makefile for `libft`

#### Overview
The Makefile automates the compilation and management of the `libft` library, which includes various utility functions. It defines the rules and dependencies for building the library, cleaning up generated files, and handling bonus files.

#### Makefile Structure
The Makefile is structured into several sections, each serving a specific purpose:

1. **Variable Definitions**: Defines variables for the library name, source files, object files, compiler, flags, and messages.
2. **Rules**: Specifies the commands to compile the source files, create the library, and clean up generated files.

#### Variable Definitions
```makefile
NAME = libft.a
SOURCES = ft_isalpha.c ft_isdigit.c ft_isalnum.c
SOURCES += ft_isascii.c ft_isprint.c ft_strlen.c
SOURCES += ft_tolower.c ft_toupper.c
SOURCES += ft_memset.c ft_bzero.c ft_memcpy.c
SOURCES += ft_memmove.c ft_strlcpy.c ft_strlcat.c
SOURCES += ft_strchr.c ft_strrchr.c ft_strncmp.c
SOURCES += ft_memchr.c ft_memcmp.c ft_strnstr.c
SOURCES += ft_atoi.c ft_calloc.c ft_strdup.c
SOURCES += ft_substr.c ft_strjoin.c ft_strtrim.c
SOURCES += ft_split.c ft_itoa.c ft_strmapi.c ft_striteri.c
SOURCES += ft_putchar_fd.c ft_putstr_fd.c ft_putendl_fd.c
SOURCES += ft_putnbr_fd.c
SOURCES += ft_lstnew.c ft_lstadd_front.c ft_lstsize.c
SOURCES += ft_lstlast.c ft_lstadd_back.c ft_lstdelone.c
SOURCES += ft_lstclear.c ft_lstiter.c ft_lstmap.c
BONUS_SOURCES = ft_lstnew_bonus.c ft_lstadd_front_bonus.c ft_lstsize_bonus.c
BONUS_SOURCES += ft_lstlast_bonus.c ft_lstadd_back_bonus.c ft_lstdelone_bonus.c
BONUS_SOURCES += ft_lstclear_bonus.c ft_lstiter_bonus.c ft_lstmap_bonus.c

OBJECTS = ${SOURCES:.c=.o}
BONUS_OBJECTS = ${BONUS_SOURCES:.c=.o}

RM = @rm -f
CC = @clang
CFLAGS = -Wall -Wextra -Werror
MSG1 = @echo "Compiled ✔︎"
MSG2 = @echo "Cleaned ✔︎"
ARCHIVE = @ar -rc
```

#### Rules
```makefile
all: $(NAME)

$(NAME): $(OBJECTS)
	$(ARCHIVE) $(NAME) $(OBJECTS)
	$(MSG1)

bonus: $(BONUS_OBJECTS)
	$(ARCHIVE) $(NAME) $(BONUS_OBJECTS)
	$(MSG1)

clean:
	$(RM) $(OBJECTS) $(BONUS_OBJECTS)
	$(MSG2)

fclean: clean
	$(RM) $(NAME)
	$(MSG2)

re: fclean all
```

#### Detailed Explanation
1. **Variable Definitions**:
   - `NAME`: The name of the static library to be created (`libft.a`).
   - `SOURCES`: List of source files to be compiled.
   - `BONUS_SOURCES`: List of bonus source files to be compiled.
   - `OBJECTS` and `BONUS_OBJECTS`: Lists of object files generated from the source files.
   - `RM`: Command to remove files.
   - `CC`: Compiler to be used (`clang`).
   - `CFLAGS`: Compiler flags (`-Wall -Wextra -Werror`).
   - `MSG1` and `MSG2`: Messages to be displayed after compilation and cleaning.
   - `ARCHIVE`: Command to create the static library.

2. **Rules**:
   - `all`: Default rule to build the library.
   - `$(NAME)`: Rule to create the library from object files.
   - `bonus`: Rule to create the library with bonus object files.
   - `clean`: Rule to remove object files.
   - `fclean`: Rule to remove object files and the library.
   - `re`: Rule to clean and rebuild the library.

#### Visual Explanation
1. **Initial Setup**:
   - Define variables for the library name, source files, object files, compiler, flags, and messages.

2. **Compilation Process**:
   - Compile source files into object files using the compiler and flags.
   - Create the static library `libft.a` from the object files.

3. **Bonus Compilation**:
   - Compile bonus source files into object files.
   - Create the static library `libft.a` from the bonus object files.

4. **Cleaning Up**:
   - Remove object files using the `clean` rule.
   - Remove object files and the library using the `fclean` rule.

5. **Rebuilding**:
   - Clean and rebuild the library using the `re` rule.

#### Situations Where the Makefile is Useful
- **Automating Compilation**: Automates the process of compiling source files and creating the library.
- **Managing Dependencies**: Ensures that only the necessary files are recompiled when changes are made.
- **Cleaning Up**: Provides rules to clean up generated files, keeping the workspace tidy.
- **Handling Bonus Files**: Includes rules to handle bonus files separately, allowing for flexible compilation options.
- **Rebuilding**: Simplifies the process of cleaning and rebuilding the entire library.