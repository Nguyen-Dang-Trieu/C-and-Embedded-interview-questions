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
    printf("\n Size of Structure = %ld bytes\n\n",sizeof(InfoData));
    return 0;
}
~~~
**Output:** 12 bytes
<p align="center">
    <img src="./Images/1.jpg" width="800px" alt="">
</p>

-------------------
#### 2. 
~~~cpp
#include <stdio.h>
typedef struct
{
    int A;
    char B;
    char C;
} InfoData;
int main(int argc, char *argv[])
{
    //Calculate size of structure
    printf("\n Size of Structure = %ld bytes\n\n",sizeof(InfoData));
    return 0;
}
~~~
**Output:** 8 bytes
<p align="center">
    <img src="./Images/2.png" width="800px" alt="">
</p>

-------------------
#### 3. 
~~~cpp
#include <stdio.h>
typedef struct
{
    double A; // 8-byte
    char B;   // 1-byte
    char C;   // 1-byte
} InfoData;
int main(int argc, char *argv[])
{
    //Calculate size of structure
    printf("\n Size of Structure = %ld bytes\n\n",sizeof(InfoData));
    return 0;
}
~~~
**Output:** 16 bytes
<p align="center">
    <img src="./Images/3.png" width="800px" alt="">
</p>
