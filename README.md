# ft_printf

For this project, I set out to reimplement printf(), one of the most commonly used functions in C. The main goal was to handle a variable number of arguments using variadic functions.

My ft_printf() function supports several format specifiers, including:

    %c for characters
    %s for strings
    %p for pointers (in hexadecimal format)
    %d and %i for integers
    %u for unsigned integers
    %x and %X for hexadecimal numbers (lowercase and uppercase)
    %% to print a percent sign

The project required managing compilation with a Makefile and adhering to specific constraints, such as using only allowed system functions like malloc, free, write, and the variadic function macros (va_start, va_arg, va_copy, va_end).
