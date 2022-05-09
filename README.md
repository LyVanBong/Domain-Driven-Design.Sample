# Domain Driven Design
## Giới thiệu
- Phương pháp DDD bao gồm các bước:
  - Phần tích nghiệp vụ - domain model
  - Định nghĩa ngữ cảnh - bounded
  - Định nghĩa đối tượng - entities
  - Tập hợp - aggregate
  - Dịch vụ - service
## Khái niệm
- Domain model
  - Core Domains - nghiệp vụ cốt lỗi, cơ bản nhất
  - Sub Domains - nghiệp vu có tính chất phụ trợ
- Việc chia tách này là tạo ra được những phạm vi ngữ cảnh - bounded context, giúp xác định rõ ranh giới giữa các nghiệp vụ, đồng thời thể hiện được chính xác ý nghĩa của những thực thể entity trongmooix phạm vi đó
- Entity được định nghĩa là các đối tượng mang dữ liệu với khả năng định danh duy nhất.
- Value object: là các đối tượng chứa dữ liệu đơn thuần
- Việc truy cập các đối tượng thông tin entity hay aggredate thường được đóng gói qua một lớp trung gian - repository. Việc đóng gói này giảm tính sự phụ thuộc của mô hình nghiệp vụ vào công nghệ lưu trữ, và nâng cao khả năng nâng cấp, thay thế công nghệ khi cần thiết
- Service là những quy trình hoạt động nghiệp vụ, chính sách doanh nghiệp ..., liên quan đến nhiều đối tượng khác nhau. Do đó các đối tượng service có tính chất stateless - các hoạt động service thực thi và không lưu giữ lại bất kì trạng thái nào
## Kiến trúc
- Sau khi phân tích các phạm vi ngữ cảnh, xác định các đối tượng nghiệp vụ bên trong chúng, bước tiếp theo là định nghiã và xây dựng những microservices tương ứng.
- Theo phương pháp DDD để tập trung vào việc xây dựng mô hình nghiệp vụ đồng thời giảm thiểu sự phụ thuộc đối với những thành phần khác của ứng dụng, mỗi service được chia thành nhiều lớp - Layers
- Kiến trúc multi-layers bao gồm
  - Domain layer
  - Application layer
  - Infrastructure layer
  ![image](https://user-images.githubusercontent.com/87922239/165467465-f5574f65-8637-41d2-8162-f1b01e87795a.png)
- Domain layer: là thành phần quan trọng nhất trong kiến trúc bởi việc đóng gói các quy tắc và mô hình nghiệp vụ. Tầng nghiệp vụ này có các đặc điểm:
  - Biểu diễn mô hình nghiệp vụ qua entities dưới hình thức các lớp _POJO_
  > POJO (Plan old java object) là thuật ngữ để chỉ các lớp đối tượng mang ý nghĩa logic đơn thuần, không ràng buộc vào ngôn ngữ hay framework cụ thể
  - Kiểm soát và thể hiện trạng thái hoạt động nghiệp vụ
  - Sử dụng domain envent để thông báo cho các module khác khi một sự kiện xẩy ra
  - Hoạt động độc lập với tầng lưu trữ vật lý, không phụ thuộc trực tiếp vào ORM framework
- Application layer: Chức năng chính của tầng này là quản lý các tác vụ yêu cầu từ bên ngoài và chuyển giao - delegate các thực thi nghiệp vụ xuống tầng Domain.
  - Presentation interface - cung cấp chức năng ứng cho phía client
  - Application interface - giao tiếp ứng dụng với những services khác
- Infrasturcture layer: làm việc trực tiếp với hạ tầng công nghệ của hệ thống phần mềm. các chức năng chính của tầng này bao gồm:
  - Truy vẫn, thay đổi thông tin trong cơ sở dữ liệu
  - Quản lý dữ liệu trên vùng nhớ tạm thời (cache data)
  - Bảo mật, giám sát, lưu trữ thông tin hoạt động (log, monitor)

[*Domain-Driven Design*](https://microservicesvn.com/docs/arch/ddd.html)

[*Domain Driver Design & Event Driven Architecture*](https://tungexplorer.me/2020/01/Other/DDD_EventDrivenArchitecture/)

[*Ebook Learning Domain-Driven Design*](https://github.com/LyVanBong/DomainDrivenDesign.Sample/blob/master/Resources/khononov_vlad_learning_domaindriven_design_aligning_software.pdf)
