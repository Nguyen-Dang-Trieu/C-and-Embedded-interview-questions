# C and Embedded interview questions ?

#### 1. What do you understand by **Wild Pointer**? How is it different from **Dangling Pointer**?
A _`Wild Pointer`_ is an uninitialized pointer (i.e. a pointer that does not store any valid address in it nor a NULL value) so by default they will hold some set location remember at will and if we try to perform any operation using them then it may cause our program to crash.

`NOTE:` If we use the free() function to free a wild pointer, we should be very careful because we cannot know whether the pointer is pointing to an important data area or not??
_Example:_ Program causing error
~~~cpp
#include <stdio.h>

int main()
{
    int *ptr; // wild pointer storing some random memory address

    // incorrect way of assigning values
    *ptr = 9; // this should not be done

    printf("The value is %d", *ptr); // trying to print the value

    return 0;
}
~~~
Instead of this, the above code can be written as
~~~cpp
#include <stdio.h>

int main()
{
    int num = 9; // initializing an int variable

    int *ptr = &num; // initializing an int pointer with a meaningful address

    printf("The value is %d", *ptr); // printing the value

    return 0;
}
~~~
------------------------------

The pointers pointing to a deallocated memory block are known as `Dangling Pointers`.

Reference: https://www.scaler.com/topics/c/dangling-pointer-in-c/
