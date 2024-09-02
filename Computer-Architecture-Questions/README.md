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
    <img src="./Images/Example.png" width="500px" alt="">
</p>

### Q2. Write C code to check for the endianness of the system
