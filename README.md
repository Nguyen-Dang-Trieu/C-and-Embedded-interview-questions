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

#### 2. How to access the fixed memory location in embedded C?
~~~cpp
//Memory address, you want to access
#define RW_FLAG 0x1FFF7800

//Pointer to access the Memory address
volatile uint32_t *flagAddress = NULL;

//variable to stored the read value
uint32_t readData = 0;

//Assign addres to the pointer
flagAddress = (volatile uint32_t *)RW_FLAG;

//Write value to the memory
*flagAddress = 12; // Write

//Read value from memory
readData = *flagAddress;
~~~
