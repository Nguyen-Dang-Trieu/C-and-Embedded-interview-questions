# Structure padding questions in C

#### 1. 
~~~cpp
#include <stdio.h>
typedef struct
{
    char A;
    int B;
    char C;
} InfoData;
int main(int argc, char *argv[])
{
    //Calculate size of structure
    printf("\n Size of Structure = %d\n\n",sizeof(InfoData));
    return 0;
}
~~~
Output:
