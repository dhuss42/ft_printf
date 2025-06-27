# ft_printf

## Contents

1. [Project Overview](#1-Project-overview)
2. [Varadic functions](#2-Varadic-functions)
3. [Logic](#3-Logic)
4. [How to create the libftprintf.a library](#4-How-to-create-the-libftprintf.a-library)

## 1. Project overview

For this project, I set out to reimplement printf(), one of the most commonly used functions in C. The main goal was to handle a variable number of arguments using variadic functions.

My ft_printf() function supports several format specifiers, including:

`%c` for characters  
`%s` for strings  
`%p` for pointers (in hexadecimal format)  
`%d` and `%i` for integers  
`%u` for unsigned integers  
`%x` and `%X` for hexadecimal numbers (lowercase and uppercase)  
`%%` to print a percent sign  

## 2. Varadic functions

Variadic functions can accept a variable number of arguments. While the first arguments are fixed, the remaining arguments can vary in number and type.

To handle these variable arguments, the `<stdarg.h>` library provides macros and the va_list type.  

Use the `va_list` type to declare a variable that will store the information needed to retrieve the additional arguments.  

`va_start(list, last_fixed_arg)` initializes the va_list to start retrieving arguments from the variable arguments section. The second argument must be the last fixed parameter in your function’s signature.

`va_arg(list, type)` retrieves the next argument from the va_list. It must be called repeatedly to access each argument.

Once all arguments have been processed, you must call `va_end(list)` to clean up the va_list. This ensures any resources used by va_list are properly released.

## 3. Logic 

In my implementation of ft_printf, I iterated over the given format string character by character. As long as I did not encounter the format symbol %, I simply printed each character using my ft_putchar function. When I encountered %, I checked the following character to determine the expected type of the next argument. For example, if the character after % was s, I expected the next argument to be a string and printed its content using ft_putstr. Similarly, for other specifiers like d or i, I printed the corresponding integer with ft_putnbr, and for pointers, I used ft_putptr.

Throughout this process, I kept a counter to track the total number of characters I printed, including both the literal characters from the format string and the converted arguments. In the end, I returned this count as an int, just like the standard printf does.

## 4. How to create the libftprintf.a library

git clone repository into your project
```
git clone https://github.com/dhuss42/ft_printf.git ft_printf
cd ft_printf
make
```

add ft_printf.h to your files or header file  
```
# include "ft_printf/ft_printf.h"
```
