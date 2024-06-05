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
    printf("\n Size of Structure = %d bytes\n\n",sizeof(InfoData));
    return 0;
}
~~~
Output: 12 bytes
<p align="center">
    <img src="./Images/Vi_du_2.png" width="500px" alt="">
</p>
