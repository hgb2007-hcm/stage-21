# (Bài tập tổng hợp) Hành Trình Xử Lý 1 Lỗi Cài Đặt Thật

## ***PHẦN 1 – Googling đúng cách***

***Giải thích vì sao câu hỏi "văn nói" ở mục 3b khiến Google trả về kết quả kém chất lượng****

Câu hỏi "tại sao em cài node xong mà gõ npm nó không nhận vậy thầy ơi" là một Bad Query vì mang nặng tính giao tiếp tự nhiên và cảm thán ("em", "thầy ơi", "vậy ạ"). Google là máy tìm kiếm từ khóa chứ không có cảm xúc hay khả năng hiểu ngữ cảnh tâm sự. Khi nhận câu này, thuật toán sẽ đi tìm các bài viết hỏi đáp diễn đàn lăng nhăng có chứa các từ ngữ xã giao đó, dẫn đến việc trả về kết quả rác, hoàn toàn lạc trôi khỏi lỗi kỹ thuật thực tế.

***Bóc tách lỗi ở mục 3a theo 3 thành phần cốt lõi***

***Tên phần mềm / Hệ điều hành***

- Node.js / npm / Windows 11

***Mã lỗi nguyên văn***

- 'npm' is not recognized as an internal or external command, operable program or batch file.

***Thao tác đang làm***

- kiểm tra phiên bản bằng lệnh npm -v trong terminal

***Viết 3 câu truy vấn Google tối ưu (mỗi câu dùng đúng 1 toán tử yêu cầu)***

- Câu 1 (Dùng site: giới hạn trong StackOverflow):site:stackoverflow.com "npm is not recognized" node.js windows

- Câu 2 (Dùng ngoặc kép "" cho lỗi nguyên văn - Exact Match):"npm is not recognized as an internal or external command"

- Câu 3 (Dùng dấu trừ - để loại trừ các bài viết cũ/không liên quan):npm is not recognized windows 11 node.js -xp -vista

## ***PHẦN 2 – Thẩm định StackOverflow***

***Khi mở một trang StackOverflow mới, bạn thực hiện lần lượt các bước sau:***

- Bỏ qua phần mô tả câu hỏi dài dòng của người đăng.

- Cuộn thẳng xuống khu vực Answers.

- Tìm ngay câu trả lời có tích xanh (Accepted Checkmark ✓) hoặc có số Upvotes cao nhất.

- Tập trung đọc trực tiếp đoạn mã lệnh trong khung Code Block để áp dụng.

## ***PHẦN 3: Viết Bug Report chuẩn để nhờ hỗ trợ***

***Tin nhắn "Kém" (Mù mờ, thiếu ngữ cảnh)***

"Trợ giảng ơi cứu em với, máy em bị lỗi gõ npm không chạy được, em làm mọi cách rồi mà vẫn không được."

***Tin nhắn chuẩn theo Bug Reporting Framework 4 bước***

**Context:** Em vừa cài mới Node.js trên laptop Windows 11 để học lập trình web và đang dùng VS Code Terminal.

**Expected:** Khi gõ lệnh npm -v, Terminal phải trả về số phiên bản của npm (ví dụ: 10.x.x).

**Actual:** Terminal báo lỗi không nhận diện lệnh và em đã thử thêm đường dẫn vào biến môi trường PATH theo hướng dẫn trên mạng nhưng vẫn không được.

**Log & Screenshot:** 'npm' is not recognized as an internal or external command, operable program or batch file. (Kèm theo hình ảnh chụp màn hình terminal)