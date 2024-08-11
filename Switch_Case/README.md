# Source of information
- [Từ Q1 -> Q4](https://www.youtube.com/watch?app=desktop&v=U4V3lMsz93k)
- [Từ Q5 -> Q8](https://www.youtube.com/watch?v=88TNyNoZAtY)

## Q1. What is the output if 1 is entered ?
~~~cpp
#include <stdio.h>

int main()
{
    double ch;
    printf("enter a value between 1 to 2: ");
    scanf("%lf", &ch);
    switch(ch){
        case 1:
           printf("1");
           break;
        case 2:
           printf("2");
           break;
    }

    return 0;
}
~~~
**Output:**
~~~
main.c: In function ‘main’:
main.c:16:12: error: switch quantity not an integer
   16 |     switch(ch){
      |  
~~~
**Reason:**

`switch` chỉ hoạt động với các giá trị kiểu nguyên `(integer)`.

`Chỉ` có thể `sử dụng` các kiểu dữ liệu sau đây trong biểu thức `switch`:
- int
- char
- short
- long
- enum
## Q2. What is the output if 1 is entered ?
~~~cpp
#include <stdio.h>

int main()
{
    int ch;
    printf("enter a value between 1 to 2: ");
    scanf("%d", &ch);
    switch(ch){
        case 1:
           printf("1\n");
        default:
           printf("2\n");
    }
    return 0;
}
~~~
If `input = 1`:  
~~~
1
2
~~~
If `input khác 1`: 
~~~
2
~~~
**NOTE:** 
Các câu lệnh bên trong case sẽ được `kết thúc` bởi câu lệnh `break`. Nếu không có câu lệnh break thì khi code trong nhánh nào được thực hiện, `switch case` sẽ không kết thúc ngay như else if mà sẽ thực hiện luôn các
câu lệnh trong các rẽ nhánh bên dưới. [Trích dẫn](https://blog.28tech.com.vn/c-switch-case)
## Q3. What is the output of this C code ?
~~~cpp
#include <stdio.h>

int main()
{
    int a = 1, b = 1;
    switch (a)
    {
        case a*b:
           printf("yes");
        case a-b:
           printf("no\n");
           break;
    }
    return 0;
}
~~~
**Output:**
~~~
main.c: In function ‘main’:
main.c:16:9: error: case label does not reduce to an integer constant
   16 |         case a*b:
      |         ^~~~
main.c:18:9: error: case label does not reduce to an integer constant
   18 |         case a-b:
      |         ^~~~
~~~

**Reason:** </br>
Lỗi vì các biểu thức trong câu lệnh `switch` và `case` phải là các hằng số nguyên  hoặc các giá trị không thay đổi `(constant expressions)`. Trong đoạn code, các biểu thức a*b và a-b không phải là hằng số, 
chúng là các biểu thức toán học phụ thuộc vào giá trị của biến a và b. Điều này không được phép trong C.
## Q4. What will be the output of the following code?
~~~cpp
#include <stdio.h>

int main()
{
    int i;
    for(i = 2; i < 10; i++){
        switch(i){
            case 1: i+=1;
            case 2: i+=2;
            case 4: i+=1;
            default: i+=3;
            break;
        }
        printf("%d\n", i);
    }
    return 0;
}
~~~
**Output:**
~~~
8
12
~~~
