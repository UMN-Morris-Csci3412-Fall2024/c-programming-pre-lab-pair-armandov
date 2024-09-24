# Leak report

_Use this document to describe whatever memory leaks
you find in `clean_whitespace.c` and how you might fix
them. You should also probably remove this explanatory
text._
In the check_whitespace.c program, we found a problem where the program was using memory but not giving it back when it was done with it. This happened in the strip function, which removes spaces from the front and back of a string. The function created new space in memory to store the cleaned up string, but it didn’t clean up that space after it was used, which caused a memory leak. Over time, this could make the program use more memory than it should.fixing this, we added a line in the tests to give back the memory after the program was done with it. For example, in one of the tests, we added this code, free((void *)result); This made sure that the memory used by the strip function was cleaned up. After adding this, we checked the program again using Valgrind, and it confirmed that the memory leak problem was fixed.