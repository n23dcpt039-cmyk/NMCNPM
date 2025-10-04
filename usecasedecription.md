# 📑 Use Case Description – Hệ thống Hub media bán lẻ đa kênh cho mỹ phẩm

------------------------------------------------------------------------

## Use Case 1: Quản lý nội dung số

**Use Case ID:** UC-01  
**Actor:** Admin, Content Creator  
**Trigger:** Actor chọn chức năng “Quản lý nội dung”.

**Description:**  
Cho phép người dùng tạo, chỉnh sửa, duyệt và gắn thẻ nội dung số (bài viết, hình ảnh, video) để phục vụ truyền thông đa kênh.

**Preconditions:**  
1. Actor đã đăng nhập hệ thống.  
2. Hệ thống hoạt động ổn định.

**Postconditions:**  
1. Nội dung được lưu và sẵn sàng xuất bản.  
2. Nếu lỗi, hệ thống thông báo và không lưu thay đổi.

**Basic Flow:**  
1. Actor chọn “Tạo/Sửa nội dung”.  
2. Nhập thông tin nội dung (tiêu đề, mô tả, media).  
3. Hệ thống lưu nội dung vào CSDL.

**Alternative Flow:**  
- UC-01.AC.1: Actor gắn thẻ nội dung theo chủ đề → hỗ trợ phân loại và tìm kiếm.

**Exception Flow:**  
- UC-01.EX.1: Thiếu thông tin bắt buộc → hệ thống hiển thị cảnh báo.  
- UC-01.EX.2: Lỗi kết nối DB → lưu thất bại.

------------------------------------------------------------------------

## Use Case 2: Xuất bản đa kênh

**Use Case ID:** UC-02  
**Actor:** Admin, Content Creator  
**Trigger:** Actor chọn “Xuất bản nội dung”.

**Description:**  
Cho phép người dùng xuất bản nội dung lên các nền tảng như Web, Facebook, Zalo, TikTok, YouTube.

**Preconditions:**  
- Nội dung đã được duyệt và hợp lệ.

**Postconditions:**  
- Nội dung hiển thị trên các kênh đã chọn.

**Basic Flow:**  
1. Actor chọn kênh xuất bản.  
2. Hệ thống gửi nội dung qua API tương ứng.  
3. Ghi nhận trạng thái xuất bản.

**Exception Flow:**  
- UC-02.EX.1: Lỗi xác thực API → hệ thống thông báo lỗi.  
- UC-02.EX.2: Kênh không phản hồi → đánh dấu thất bại.

------------------------------------------------------------------------

## Use Case 3: Tích hợp API mạng xã hội

**Use Case ID:** UC-03  
**Actor:** Hệ thống  
**Trigger:** Có nội dung mới hoặc tin nhắn từ người dùng.

**Description:**  
Hệ thống tự động phản hồi tin nhắn, chia sẻ nội dung lên mạng xã hội thông qua API Zalo OA và Facebook Page.

**Preconditions:**  
- Hệ thống đã kết nối API thành công.

**Postconditions:**  
- Nội dung được chia sẻ hoặc phản hồi được gửi đi.

**Basic Flow:**  
1. Hệ thống nhận sự kiện (tin nhắn, nội dung mới).  
2. Gửi yêu cầu đến API.  
3. Nhận phản hồi và cập nhật trạng thái.

**Exception Flow:**  
- UC-03.EX.1: Token hết hạn → hệ thống yêu cầu xác thực lại.  
- UC-03.EX.2: Lỗi mạng → retry hoặc thông báo lỗi.

------------------------------------------------------------------------

## Use Case 4: Phân tích hiệu quả truyền thông

**Use Case ID:** UC-04  
**Actor:** Admin, Manager  
**Trigger:** Actor chọn “Xem phân tích”.

**Description:**  
Hệ thống hiển thị báo cáo hiệu quả truyền thông theo từng kênh, nội dung, thời gian.

**Preconditions:**  
- Actor đã đăng nhập.

**Postconditions:**  
- Báo cáo hiển thị hoặc xuất ra file.

**Basic Flow:**  
1. Actor chọn loại báo cáo.  
2. Nhập điều kiện lọc (thời gian, kênh).  
3. Hệ thống xử lý và hiển thị kết quả.

**Exception Flow:**  
- UC-04.EX.1: Không có dữ liệu phù hợp → hiển thị “Không có dữ liệu”.

------------------------------------------------------------------------

## Use Case 5: Quản lý quyền riêng tư & tuân thủ

**Use Case ID:** UC-05  
**Actor:** Admin  
**Trigger:** Người dùng gửi consent hoặc truy cập hệ thống.

**Description:**  
Hệ thống ghi nhận sự đồng ý của người dùng, lưu log truy cập để đảm bảo tuân thủ chính sách bảo mật.

**Preconditions:**  
- Người dùng đã tương tác với hệ thống.

**Postconditions:**  
- Consent và log được ghi nhận.

**Basic Flow:**  
1. Người dùng gửi consent.  
2. Hệ thống lưu thông tin vào CSDL.  
3. Ghi log truy cập theo thời gian thực.

**Exception Flow:**  
- UC-05.EX.1: Lỗi ghi log → hệ thống cảnh báo và lưu tạm.