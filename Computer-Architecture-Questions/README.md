### Q1. What is Endianness? Little and Big ❓
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

### Q2. Write a C program to convert decimal to binary and hexa ❓
~~~c
#include <stdio.h>
#include <string.h>

// Hàm chuyển đổi thập phân sang nhị phân
void Convert_Decimal_to_Binary(int data) {
    char str[33] = "";                          //  32 bit + '\0'
    int index = 0;

    while (data > 0) {
        str[index++] = (data % 2) ? '1' : '0';  // Lưu kết quả bit trực tiếp vào chuỗi
        data = data / 2;
    }

    // Đảo ngược chuỗi 
    int len = strlen(str);
    for (int i = 0; i < len / 2; i++) {
        char temp = str[i];
        str[i] = str[len - 1 - i];
        str[len - 1 - i] = temp;
    }

    printf("Chuỗi nhị phân: %s\n", str);
}

void Convert_Decimal_to_Hexa(int data) {
    char str[10] = "";  
    char temp[2];                               // Chuỗi tạm thời để chứa ký tự chuyển đổi
    
    while (data != 0) {
        int remainder = data % 16;
        data = data / 16;
        
        if (remainder < 10) {
            temp[0] = '0' + remainder;         // Chuyển đổi số thành ký tự
        } else {
            temp[0] = 'A' + (remainder - 10);  // Chuyển đổi 10-15 thành 'A'-'F'
        }
        
        temp[1] = '\0';  
        strcat(str, temp);                     // Nối temp vào chuỗi str
    }
    
    // Đảo ngược chuỗi
    int len = strlen(str);
    for (int i = 0; i < len / 2; i++) {
        char tempChar = str[i];
        str[i] = str[(len - 1) - i];
        str[(len - 1) - i] = tempChar;
    }

    printf("Chuỗi: %s\n", str);
}

int main()
{
    int a = 30;
    Convert_Decimal_to_Binary(a);
    int b = 923;
    Convert_Decimal_to_Hexa(b);
    return 0;
}
~~~
**OUTPUT:**
~~~
Chuỗi nhị phân: 11110
Chuỗi: 39B
~~~

### Q3. Write C code to check for the endianness of the system ❓
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
