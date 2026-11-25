## Chuẩn bị trước buổi demo

Mở ba phiên trình duyệt độc lập để giữ đăng nhập theo vai trò. Nên để phiên sinh viên mở sẵn ở Thông báo khi chuyển sang demo TC-11.
| Vai trò | Tài khoản có sẵn | Mật khẩu demo |
| --- | --- | --- |
| Sinh viên | MSSV 2410001 | User@123 |
| Admin | admin@emobility.vn | Admin@123 |
| Operator | operator@emobility.vn | Operator@123 |

Quy ước dữ liệu: dùng H01 – Ga Metro Đại học Quốc gia cho H1 và V001 cho V01. Seed hiện tại dùng MSSV 2410001 thay cho 2210001, và pin ban đầu của V001 là 50%. Nếu cần tái hiện đúng đầu vào TC-04, vào Quản trị → Xe → Sửa V001 và đặt pin 80% trước buổi demo. Nếu đã qua 08:00, dời giờ đặt xe và đặt chỗ đỗ sang khung giờ phù hợp với lúc trình bày.

## Trình tự màn hình để demo với giảng viên

| Ca | Màn hình và thao tác | Kết quả cần chỉ trên màn hình |
| --- | --- | --- |
| TC-01 · Đăng nhập | Đăng nhập → nhập MSSV 2410001 và mật khẩu → bấm Đăng nhập. | Hệ thống mở trang Trạm của sinh viên và hiển thị tài khoản đã đăng nhập. |
| TC-02 · Trạng thái Hub | Trạm → Danh sách trạm → chọn H01 đã chuẩn bị ở mức tải WARNING. | Chỉ lần lượt chỗ đỗ trống, cổng sạc trống, xe sẵn sàng và nhãn WARNING. Tài liệu dùng 85%. Với seed H01 có 16 ô đỗ và cổng cộng lại, nếu hàng chờ trống thì 14/16 tài nguyên bận cho khoảng 88%, vẫn nằm trong dải cảnh báo từ 80% đến dưới 95%. |
| TC-03 · Thêm xe | Admin → Quản trị → Xe → Thêm xe. Nhập mã V20, loại E_BIKE, pin 100%, trạm H01 → Lưu. | V20 xuất hiện trong danh sách với trạng thái AVAILABLE. Nếu đã dùng mã này khi chạy thử, chọn mã mới và ghi rõ dữ liệu thay thế. |
| TC-04 · Tìm và đặt xe | Sinh viên → Thuê xe. Chọn H01, Xe đạp điện, pin tối thiểu 50% → Tìm xe → Đặt xe cho V001 trong khung 08:00–10:00 hoặc một khung tương đương. | V001 xuất hiện trong kết quả ban đầu. Sau khi đặt, Lượt đặt của tôi hiển thị RESERVED. Tìm lại bằng phiên sinh viên thứ hai để thấy V001 đã rời danh sách xe khả dụng. Sau khi trình bày, có thể Hủy lượt đặt để dùng lại V001 cho TC-09. |
| TC-05 · Đặt chỗ và check-in | Sinh viên → Đỗ xe. Chọn xe cá nhân 59X1-123.45, H01 và ô trống → đặt chỗ → Check-in. Để thao tác ngay khi trình bày, chọn giờ bắt đầu trong vòng 30 phút tới. | Ô đỗ chuyển RESERVED sau khi đặt. Sau check-in, lượt đặt là CHECKED_IN và ô đỗ là OCCUPIED. |
| TC-06 · Vào hàng chờ sạc | Chuẩn bị H01 có tất cả cổng đang sạc và hai yêu cầu chờ. Sau đó gửi yêu cầu thứ ba. Dùng Demo đồ án → Tạo yêu cầu sạc với Operator nếu dùng xe chung. Dùng Sinh viên → Sạc xe với xe cá nhân nếu cần giảng viên xem kết quả từ phía người dùng. | Yêu cầu mới là WAITING, vị trí 3. Chuẩn bị hai yêu cầu trước có mức ưu tiên bằng hoặc cao hơn yêu cầu mới, vì hệ thống xếp theo ưu tiên. V05 trong tài liệu là xe chung và bản hiện tại chỉ cho Operator đăng ký sạc xe chung tại Hub của xe. |
| TC-07 · Phân bổ hai cổng sạc | Operator → Lịch sạc. Chuẩn bị đúng hai cổng khả dụng và ba yêu cầu chờ đủ điều kiện gán. Chọn Hub → Tạo lịch sạc. | Chỉ vào hai yêu cầu ASSIGNED, yêu cầu còn lại WAITING ở vị trí 1 và thông báo gán cổng phía sinh viên nếu dùng yêu cầu do sinh viên tạo. Mức ưu tiên có chênh lệch với tài liệu, xem phần dưới. |
| TC-08 · Điều phối xe | Operator → Đội xe → xem Mất cân bằng và Gợi ý điều phối → bấm Áp dụng. Có thể dùng H01 làm trạm thiếu và H03 làm trạm dư với seed ban đầu. | Hiện nhãn thiếu/dư, lệnh điều phối được tạo và các xe trong lệnh chuyển IN_TRANSIT. Nếu cần đúng 5 xe và đề xuất hiện số khác, nhập 5 ở Tạo lệnh điều phối khi trạm nguồn đủ xe. Khi đó bạn đang demo tạo lệnh thủ công. |
| TC-09 · Báo hỏng phanh | Operator → Sự cố → chọn V001 đang AVAILABLE, loại VEHICLE_FAULT, tiêu đề “V001 hỏng phanh” → Báo cáo → Kiểm tra → Chuyển bảo trì → Đã xử lý. | Lịch sử hiện REPORTED → INVESTIGATING → MAINTENANCE → RESOLVED. Mở Đội xe để đối chiếu V001 ở MAINTENANCE khi sửa và AVAILABLE sau khi xử lý. |
| TC-10 · Mô phỏng giới hạn công suất | Operator → Mô phỏng → chọn Giới hạn công suất (CAPACITY_LIMIT), H01, 07:00–09:00. Tài liệu chưa cho giá trị giới hạn, có thể để trống Số xe tối đa và đặt Số cổng sạc tối đa = 2 nếu H01 đang có nhiều hơn hai cổng hoạt động. Bấm Chạy mô phỏng. | Chỉ bảng tác động trước/sau và danh sách đề xuất theo ưu tiên. Mở lại Trạm H01 để xác nhận số cổng vận hành thực tế giữ nguyên. |
| TC-11 · Gửi cảnh báo quá tải | Khi H01 đã ở OVERLOADED, mở Operator → Giám sát → Tạo cảnh báo. Chọn HUB_OVERLOAD, H01, kênh IN_APP, nhập tiêu đề “Trạm H01 quá tải” và nội dung → Gửi cảnh báo. Chuyển sang Sinh viên → Thông báo. | Operator thấy cảnh báo đã lưu và ghi nhận gửi qua IN_APP. Sinh viên thấy đúng thông báo. Bản hiện tại hiển thị trạng thái sau gửi là IN_PROGRESS. Ô ID người nhận để trống sẽ gửi cho tất cả User, nên để kiểm tra một người nhận cụ thể, điền ID tài khoản demo. |

## Hai điểm cần nói rõ khi chấm theo testcase

- TC-07 có khác biệt về mức ưu tiên. Bảng 7.4 kỳ vọng A = HIGH, B = MEDIUM, C = LOW. Với cấu hình mặc định hiện tại, A cần xe sau 20 phút nên là HIGH, B pin 10% cũng là HIGH vì ngưỡng pin thấp là 20%, còn C là MEDIUM nếu thời lượng sạc từ 90 phút trở lên và không có điều kiện ưu tiên cao hơn. Hãy cho giảng viên xem riêng mức ưu tiên thực tế và kết quả cấp hai cổng. Cần chuẩn bị sẵn hàng chờ vì backend có thể tự cấp cổng trước khi bấm Tạo lịch sạc. SmartScheduler.java
- TC-11 có khác biệt về trạng thái và phạm vi nhận. Tài liệu ghi DELIVERING → DELIVERED cho người dùng gần H01. Mã hiện tại chuyển ca sang IN_PROGRESS sau khi gửi thành công, và chọn người nhận theo ID hoặc toàn bộ User. Khi demo, dùng nhật ký gửi trên màn Operator và thông báo xuất hiện trên màn Sinh viên làm bằng chứng. Alert.java · NotificationService.java
Nếu chỉ có 8–10 phút, ưu tiên TC-04 → TC-07 → TC-09 → TC-10 → TC-11. Chuẩn bị dữ liệu sạc và quá tải trước, vì đó là hai phần phụ thuộc trạng thái hệ thống nhất. Mình đã đối chiếu hướng dẫn với bảng 7.4 và mã hiện tại. Các kết quả trong bảng là tiêu chí quan sát, chưa phải kết quả chạy thực tế vì Docker Engine không truy cập được trong phiên này.
