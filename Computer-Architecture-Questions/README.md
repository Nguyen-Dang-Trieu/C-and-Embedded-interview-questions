### Q1. What is Endianness? Little and Big
❓ **What is Endianness?** 🤔 </br>

✅ **Endianness** is the order by which `bytes` are stored in computer memory. Endianness tells us whether bytes are represented from left to right or right to left.
<p align="center">
    <img src="./Images/Endianness.png" width="500px" alt="">
</p>

❓ **How does Endianness work?**
There are two ways Endianness  allows data to be stored in memory: </br>
📌 *Little-Endian*: Store the `least significant byte` in the `smallest address`.

<p align="center">
    <img src="./Images/Little-Endian.png" width="500px" alt="">
</p>

📌 *Big-Endian*: Store the `most significant byte` in the `smallest address`.

<p align="center">
    <img src="./Images/Big-Endian.png" width="500px" alt="">
</p>

🔥 **Example:**
<p align="center">
    <img src="./Images/Example.png" width="800px" alt="">
</p>

### Q2. Write C code to check for the endianness of the system
~~~c

#include <stdio.h>

int main()
{
    printf("Kich thuoc cua unsigned int: %zu byte\n", sizeof(unsigned int));
    unsigned int value = 312784434; // 12 A4 B6 32
    void* ptr1 = &value;
    printf("Địa chỉ của biến value: %p\n", ptr1);
    
    char *ptr = (char*) &value;
    /* 
     * Ép kiểu con trỏ từ unsigned int* sang char* không thay đổi địa chỉ, chỉ thay đổi cách chương trình sẽ 
     * diễn giải dữ liệu mà con trỏ trỏ tới.
     *
     */

    if(*ptr == 32){
        printf("Little-Endian");
    }
    else if(*ptr == 12){
        printf("Big-Endian");
    }

    return 0;
}
~~~
