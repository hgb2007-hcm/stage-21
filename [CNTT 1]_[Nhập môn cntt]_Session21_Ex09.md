# Xây Dựng Prompt 3 Thành Phần Giải Mã Thông Báo Lỗi Trạm Sạc Cùng Trợ Lý AI

## ***PHẦN 1: Thiết kế Prompt 3 Thành phần Chuẩn hóa***

***Phân tích nguyên nhân làm AI bị "ngáo"***

- Thiếu ngữ cảnh trầm trọng: Câu hỏi "AI ơi phần mềm trạm sạc của tôi bị hỏng rồi làm sao đây?" là một dạng câu hỏi mơ hồ, thiếu dữ liệu đầu vào. AI không hề biết phần mềm gì, chạy trên hệ điều hành nào (Windows, Linux), hay lỗi ở chỗ nào (phần cứng, mạng, hay phân quyền).

- Cơ chế phỏng đoán mò (Hallucination): Khi không có đủ thông tin, mô hình ngôn ngữ của AI sẽ tự "điền vào chỗ trống" dựa trên dữ liệu xác suất. Nó thấy chữ "trạm sạc" nên đoán đại là lỗi dây điện, phần cứng rồi khuyên tháo vỏ sắt kiểm tra. Điều này cực kỳ nguy hiểm vì vừa làm mất thời gian, vừa dễ gây chập cháy nguy hiểm cho kỹ thuật viên tại hiện trường.

## ***PHẦN 2: Giải mã Lỗi & Kịch bản Khắc phục***

Đóng vai Trợ lý AI: Dịch và giải thích lỗi đời thường

"Chào bạn kỹ thuật viên, bạn yên tâm là phần cứng trạm sạc và dây điện không bị hỏng hóc gì đâu nhé!

- Giải thích nôm na: Lỗi UnauthorizedAccessException: Access to the path... is denied hiểu đơn giản là: Phần mềm chạy trạm sạc đang muốn mở file nhật ký session.log để ghi dữ liệu, nhưng hệ điều hành Windows 11 lại khóa cửa, không cho phép ghi.

- Nguyên nhân gốc rễ: Thư mục C:\Program Files là "vùng cấm" bảo mật của Windows. Khi phần mềm chạy bằng quyền người dùng thông thường (User), nó sẽ bị Windows chặn lại không cho tạo hay sửa file ở đây. Ứng dụng không ghi được log nên nó tự sập luôn!"*

***Ba (03) bước xử lý nhanh tại chỗ trên Windows 11***

Anh em tại trạm cứ bình tĩnh làm lần lượt 3 bước này trên máy Kiosk là trạm sạc chạy lại mượt mà ngay:

- Bước 1: Tắt hẳn phần mềm đang bị treo

   - Nhấn tổ hợp phím Ctrl + Shift + Esc để mở Task Manager.

   - Tìm tiến trình ControllerDaemon (hoặc tên phần mềm trạm sạc), nhấp chuột phải chọn End task để tắt sạch các tiến trình ẩn.

- Bước 2: Chạy phần mềm bằng quyền Admin (Run as Administrator)

   - Ra ngoài màn hình Desktop (hoặc thư mục cài đặt C:\Program Files\VoltCharge), nhấp chuột phải vào file chạy .exe của phần mềm.

   - Ra ngoài màn hình Desktop (hoặc thư mục cài đặt C:\Program Files\VoltCharge), nhấp chuột phải vào file chạy .exe của phần mềm.

 - Bước 3: Đặt quyền Admin cố định & Phân quyền ghi file (Permission)

   - Nhấp chuột phải vào file .exe $\rightarrow$ Chọn Properties $\rightarrow$ Chuyển sang tab Compatibility.

   - Tích chọn vào ô "Run this program as an administrator" $\rightarrow$ Bấm Apply $\rightarrow$ OK.(Mẹo phụ nếu vẫn lỗi: Nhấp chuột phải vào thư mục C:\Program Files\VoltCharge\data $\rightarrow$ Properties $\rightarrow$ Tab Security $\rightarrow$ Edit $\rightarrow$ Chọn User hiện tại và tích chọn ô Full control / Write để cấp quyền ghi file tuyệt đối).

***Bẫy an ninh: Xử lý Secret Key trước khi dán vào AI***

   - Cách xử lý: Nếu trong log lỗi có dính chuỗi mã bí mật như API_KEY: volt_secret_token_889922, kỹ thuật viên bắt buộc phải xóa bỏ hoặc thay thế nó thành chuỗi giả lập (ví dụ: API_KEY: [REDACTED_KEY]) trước khi nhấn gửi cho AI.

- Lý do chết người:   

  - Các công cụ AI như ChatGPT hay Gemini mặc định có thể sử dụng dữ liệu đoạn chat của người dùng để huấn luyện mô hình (AI Training Data).

  - Nếu dán thẳng API Key thật lên đó, chuỗi khóa bí mật của hệ thống VoltCharge có thể bị rò rỉ ra ngoài. Hacker hoặc kẻ gian có thể khai thác mã token này để gửi lệnh giả mạo điều khiển trạm sạc, can thiệp vào dữ liệu thanh toán hoặc chiếm quyền kiểm soát hạ tầng mạng của công ty!