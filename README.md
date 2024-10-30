# C and Embedded interview questions ?
## Reference
- https://www.geeksforgeeks.org/embedded-c-interview-questions/

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

**Reference:**
- [Dangling Pointer in C](//www.scaler.com/topics/c/dangling-pointer-in-c/)

------------------------
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
-----------------
#### 3. What will be the output of the below C program? 
~~~cpp
#include <stdio.h>

int main()
{
    char var = 10;
    void *ptr = &var;

    printf("%d %d",*(char*)ptr,++(*(char*)ptr));
    return 0;
}
~~~
Output: undefined
Explanation: Due to the sequence point the output vary on a different platform.
---------------------------
#### 4. Write a program swap two numbers without using the third variable?
**Method 1: Using Arithmetic Operators**
~~~cpp
#include <stdio.h>

int main(){
    int a = 10, b = 5;

    // algo to swap 'a' and 'b'
    a = a + b;  // a becomes 15
    b = a - b;  // b becomes 10
    a = a - b;  // fonally a becomes 5

    printf("After Swapping the value of: a = %d, b = %d\n\n", a, b);
    return 0;
}
~~~

**Method 2: Using Bitwise XOR Operator**
~~~cpp
#include <stdio.h>

/* XOR (^)
  1 xor 1 = 0
  1 xor 0 = 1
  0 xor 1 = 1
  0 xor 0 = 0
  
*/
int main(){
    int a = 10, b = 5;  // a = 0b0000 1010 , b = 0b0000 0101

    // algo to swap 'a' and 'b'
    /* a =  0000 1010
              XOR
       b =  0000 0101
     --------------------
            0000 0101 = 5 => a = a ^ b = 5
    */
    a = a ^ b;  


    /* a =  0000 0101
              XOR
       b =  0000 0101
     --------------------
            0000 0000 = 0 => b = a ^ b = 0
    */
    b = a ^ b;  


    /* a =  0000 0101
              XOR
       b =  0000 0000
     --------------------
            0000 101 = 5 => a = a ^ b = 5
    */
    a = a ^ b;  

    printf("After Swapping the value of: a = %d, b = %d\n\n", a, b);
    return 0;
~~~
-------------------
#### 5. What will be the output of the below C program? 
~~~cpp
#include <stdio.h>

#define ATICLEWORLD 0x01
#define AUTHOR      0x02
/* OR(|)
  0 or 0 = 0
  0 or 1 = 1
  1 or 0 = 1
  1 or 1 = 1 */
  
int main(){
    unsigned char test = 0x00;

    test|=ATICLEWORLD;
    test|=AUTHOR;

    if(test & ATICLEWORLD){ // dk if true khi (test & ATICLEWORLD) = 1 (= 0x01)
        printf("I am an Aticleworld");
    }
    
    if(test & AUTHOR){ // dk if true khi (test & AUTHOR) = 1 (= 0x01)
        printf(" Author");
    }
    return 0;
}
~~~
**Output:** I am an Aticleworld

#### 6. What is meant by structure padding?
*In the case of structure or union, the compiler inserts some extra bytes between the members of structure or union for the alignment, these extra unused bytes are called padding bytes and this technique is called `padding`.*

Padding has increased the performance of the processor at the penalty of memory. In structure or union data members aligned as per the size of the highest bytes member to prevent the penalty of performance.

`Note:` Alignment of data types mandated by the `processor architecture`, not by `language`. <br>
**You can see the below Articles,**
- [Struct padding questions in C](https://github.com/Nguyen-Dang-Trieu/C--and-Embedded-interview-questions/tree/main/Structure-questions)


