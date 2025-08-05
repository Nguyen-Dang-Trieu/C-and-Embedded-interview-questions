📘 I. Câu hỏi cơ bản
I²C là gì? Có những đặc điểm gì nổi bật so với UART hoặc SPI?

I²C có bao nhiêu dây? Vai trò của từng dây là gì?

I²C có thể kết nối bao nhiêu thiết bị trên cùng một bus?

Sự khác nhau giữa địa chỉ 7-bit và 10-bit trong I²C là gì?

Tại sao cần dùng điện trở pull-up cho SDA và SCL? Giá trị điển hình là bao nhiêu?

Bus arbitration trong I²C là gì?

I²C hoạt động đồng bộ hay bất đồng bộ? Vì sao?

Điểm khác biệt giữa master và slave trong I²C là gì?

🔧 II. Câu hỏi kỹ thuật chi tiết
Diễn tả một chuỗi truyền I²C từ master đến slave để ghi 1 byte.

Start và Stop condition trong I²C là gì? Được tạo ra như thế nào?

I²C ACK và NACK là gì? Khi nào thì slave gửi NACK?

Nếu một thiết bị không phản hồi trên bus I²C, bạn sẽ xử lý thế nào?

Bạn đã bao giờ gặp lỗi "bus stuck low" (SCL hoặc SDA bị kéo thấp mãi)? Làm sao để khắc phục?

Có thể giao tiếp với 2 thiết bị có cùng địa chỉ I²C không? Giải pháp?

Tốc độ I²C thông thường là bao nhiêu? Có bao nhiêu chế độ tốc độ?

💻 III. Câu hỏi về lập trình và thực tiễn
Bạn đã từng viết driver I²C ở mức register chưa?

Bạn có biết cách dùng DMA với I²C không? Lợi ích là gì?

Hàm HAL_I2C_Mem_Read() và HAL_I2C_Master_Transmit() khác nhau thế nào?

Khi dùng I²C để giao tiếp với cảm biến, bạn thường đọc giá trị bằng cách nào?

Gợi ý trả lời: ghi địa chỉ thanh ghi → đọc dữ liệu (multi-byte...)

Làm sao để debug một thiết bị không trả lời trên I²C?

Gợi ý: kiểm tra bằng logic analyzer, kiểm tra điện trở pull-up, reset slave, kiểm tra địa chỉ…

🧠 IV. Câu hỏi nâng cao
Bus recovery trong I²C là gì? Tại sao cần? Làm thế nào để implement?

Phân biệt giữa repeated start và stop/start mới trong I²C. Khi nào nên dùng?

I²C đa master hoạt động thế nào? Có cần arbitration không?

Giải thích quá trình đọc dữ liệu 3 byte từ slave như cảm biến MAX30102.

Bạn có thể tạo bit-banging I²C không? Ưu nhược điểm so với dùng hardware I²C?
