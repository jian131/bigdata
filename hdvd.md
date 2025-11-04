# VĂN THUYẾT TRÌNH - HỆ THỐNG QUẢN LÝ NHÀ THUỐC LONG CHÂU 175 TÂY SƠN

> **Thời lượng:** 15-18 phút
> **Nhóm 3 - Lớp 64HTTT4** > **Môn:** Quản trị Hệ thống Thông tin
> **Giảng viên:** ThS. Trần Hồng Diệp

---

## PHẦN MỞ ĐẦU (Phạm Năng Ân - Trưởng nhóm) - 1 phút

Kính chào thầy cô và các bạn!

Nhóm 3 - lớp 64HTTT4 xin phép được trình bày đề tài: **"Xây dựng Hệ thống Quản lý Nhà thuốc Long Châu cơ sở 175 Tây Sơn"**.

Nhóm chúng em gồm 6 thành viên:

- Phạm Năng Ân - Trưởng nhóm
- Nguyễn Ngọc Bảo Tuấn
- Phan Văn Định
- Bùi Đức Tùng
- Hoàng Văn Cường
- Đào Duy Minh

Trong bối cảnh chuyển đổi số đang diễn ra mạnh mẽ, ngành dược phẩm Việt Nam cũng đang có những bước chuyển mình quan trọng. Tuy nhiên, nhiều nhà thuốc vẫn đang gặp khó khăn trong việc quản lý hiệu quả do phụ thuộc vào phương thức thủ công, dẫn đến nhiều vấn đề về tồn kho, dịch vụ khách hàng và dự báo nhu cầu.

Xuất phát từ thực tế đó, nhóm chúng em đã chọn cơ sở Long Châu 175 Tây Sơn - một trong những nhà thuốc lớn tại Hà Nội - để nghiên cứu và đề xuất một hệ thống quản lý toàn diện, ứng dụng công nghệ AI và phân tích dữ liệu.

Bài trình bày của nhóm sẽ được chia thành 5 phần chính, bắt đầu với phần đánh giá hiện trạng.

---

## CHƯƠNG 1: ĐÁNH GIÁ HIỆN TRẠNG (Phan Văn Định) - 3 phút

### 1.1. Tổng quan thị trường dược phẩm Việt Nam

Xin chào thầy cô và các bạn, em là Phan Văn Định, phụ trách phần phân tích hiện trạng và thị trường.

Theo số liệu từ Hiệp hội Dược phẩm Việt Nam năm 2024, thị trường dược của chúng ta đang có những con số rất ấn tượng:

**Quy mô thị trường đạt 7.8 tỷ USD**, tăng trưởng 12.5% so với năm 2023. Đặc biệt, phân khúc chuỗi nhà thuốc hiện đại đang tăng trưởng nhanh nhất với tốc độ 18-20% mỗi năm.

Hành vi người tiêu dùng cũng đang thay đổi rõ rệt:

- 78% người dân chú trọng hơn đến chất lượng thuốc
- 65% lựa chọn chuỗi nhà thuốc lớn thay vì nhà thuốc nhỏ lẻ
- Đáng chú ý là 82% tự mua thuốc không kê đơn - điều này đặt ra yêu cầu cao về tư vấn dược sĩ

Công nghệ số cũng đang tạo ra những thay đổi căn bản. Đơn thuốc điện tử tăng 250% sau đại dịch, chatbot y tế được 38% người dùng tin tưởng, và 67% người dùng smartphone có ít nhất một ứng dụng sức khỏe.

### 1.2. Phân tích Long Châu và cơ sở 175 Tây Sơn

Long Châu được thành lập năm 2018 bởi FPT Retail, và chỉ trong 6 năm đã trở thành chuỗi nhà thuốc lớn nhất Việt Nam với hơn 1.100 cửa hàng, chiếm 35% thị phần.

Cơ sở 175 Tây Sơn mà nhóm em nghiên cứu có vị trí đặc biệt:

- Nằm gần Bệnh viện Bạch Mai chỉ 500m, gần Đại học Y 300m
- Phục vụ trung bình 800-1.200 khách mỗi ngày
- Doanh thu đạt 650-750 triệu đồng mỗi tháng
- Quản lý khoảng 4.200 sản phẩm dược phẩm

### 1.3. Bảy vấn đề nghiêm trọng

Tuy nhiên, qua khảo sát thực tế trong 6 tháng qua, chúng em phát hiện **7 vấn đề nghiêm trọng**:

**VẤN ĐỀ 1 - Quản lý kho kém:** Đã có 3 lần thuốc hết hạn không phát hiện kịp, gây thiệt hại 8.7 triệu đồng. Kiểm kê thủ công mất 6-8 giờ mỗi tháng.

**VẤN ĐỀ 2 - Bán hàng chậm:** Thời gian phục vụ một khách hàng lên tới 8-12 phút vì phải tìm thuốc thủ công, không có hệ thống kiểm tra tương tác thuốc tự động.

**VẤN ĐỀ 3 - CRM yếu:** Không lưu lịch sử khách hàng, mất 15-20% khách hàng tiềm năng do không có chương trình chăm sóc cá nhân hóa.

**VẤN ĐỀ 4 - Dự báo kém:** Mùa đông năm ngoái thiếu 40% thuốc cảm cúm vì không có công cụ dự báo theo mùa.

**VẤN ĐỀ 5 - Quản lý nhân sự thủ công:** Đã có 2 lần tính sai lương gây bất mãn nhân viên, thiệt hại 1.8 triệu đồng.

**VẤN ĐỀ 6 - Dữ liệu rời rạc:** Quản lý bằng 5 file Excel khác nhau, đã bị mất dữ liệu 2 lần.

**VẤN ĐỀ 7 - Hạ tầng yếu:** Không có backup tự động, không có cloud, không bảo mật.

**Tổng thiệt hại:** Trong 6 tháng qua, 7 vấn đề này gây thiệt hại **33 triệu đồng** và ảnh hưởng nghiêm trọng đến uy tín với khách hàng.

Đây chính là lý do nhóm em đề xuất xây dựng một hệ thống quản lý toàn diện. Em xin mời bạn Tuấn trình bày phần thiết kế hệ thống.

---

## CHƯƠNG 2: THIẾT KẾ HỆ THỐNG (Nguyễn Ngọc Bảo Tuấn) - 5 phút

### 2.1. Tổng quan giải pháp

Cảm ơn bạn Định. Em là Nguyễn Bảo Tuấn, phụ trách thiết kế UML và cơ sở dữ liệu.

Để giải quyết 7 vấn đề vừa rồi, nhóm em đề xuất xây dựng hệ thống với **kiến trúc 3 tầng hiện đại**:

**Tầng 1 - Presentation (Giao diện):**

- Web application cho nhân viên
- Mobile app cho quản lý và khách hàng
- POS terminal tại quầy bán hàng

**Tầng 2 - Business Logic (Xử lý nghiệp vụ):**

- 8 module chính: Inventory, POS, DDI Engine, CRM, BI Dashboard, HR, BHYT Integration, E-prescription

**Tầng 3 - Data (Dữ liệu):**

- PostgreSQL 15 cho database chính
- Redis cho cache
- Data Warehouse cho phân tích

### 2.2. Phân tích UML

Nhóm em sử dụng **ngôn ngữ UML chuẩn quốc tế** để thiết kế hệ thống, với tất cả các sơ đồ được chuyển ngữ sang tiếng Việt để dễ hiểu.

**Sơ đồ Ca sử dụng (Use Case Diagram)** mô tả 20 chức năng chính của hệ thống, phục vụ 5 tác nhân:

- Khách hàng
- Dược sĩ bán lẻ
- Thu ngân
- Thủ kho
- Quản lý

Các ca sử dụng quan trọng nhất bao gồm:

- **UC_SaleOTC:** Bán thuốc không kê đơn
- **UC_ReceiveRx:** Tiếp nhận đơn thuốc
- **UC_DDI:** Kiểm tra tương tác thuốc - cực kỳ quan trọng cho an toàn bệnh nhân
- **UC_FEFO:** Xuất kho theo nguyên tắc "hết hạn trước xuất trước"
- **UC_Reorder:** Đặt hàng tự động khi tồn kho thấp

### 2.3. Quy trình bán hàng thông minh

Cho phép em trình bày chi tiết quy trình bán hàng - đây là quy trình cốt lõi giải quyết **Vấn đề 2** về tốc độ phục vụ chậm.

**Quy trình cũ (8-12 phút):**

1. Khách đưa đơn thuốc
2. Dược sĩ đọc tay (dễ nhầm)
3. Tìm thuốc thủ công
4. Không kiểm tra tương tác
5. Tính tiền thủ công
6. Ghi sổ Excel

**Quy trình mới với AI (2-3 phút):**

_Giai đoạn 1 - Nhận dạng đơn thuốc:_

- Khách upload ảnh đơn hoặc đơn điện tử
- **OCR Engine** sử dụng AI nhận dạng chữ viết tay trong 5 giây
- Độ chính xác 95%, nếu thấp hơn sẽ yêu cầu dược sĩ kiểm tra

_Giai đoạn 2 - Kiểm tra an toàn (DDI Analysis):_

- **DDI Service** phân tích tương tác giữa các thuốc
- Kiểm tra chống chỉ định với tuổi, giới tính, thai kỳ
- Nếu phát hiện nguy hiểm (ví dụ: Warfarin + Aspirin → nguy cơ xuất huyết) → cảnh báo đỏ, yêu cầu dược sĩ can thiệp

_Giai đoạn 3 - Quản lý kho FEFO:_

- Hệ thống tự động chọn lô thuốc gần hết hạn nhất
- Giải quyết **Vấn đề 1** về thuốc hết hạn

_Giai đoạn 4 - Thanh toán và BHYT:_

- Tích hợp BHYT API, kiểm tra quyền lợi tự động
- Hỗ trợ nhiều phương thức: tiền mặt, QR code, ví điện tử
- In hóa đơn điện tử và nhãn hướng dẫn

**Kết quả:** Giảm thời gian từ 10 phút xuống 3 phút, tăng năng suất 70%, và quan trọng nhất là **đảm bảo an toàn cho bệnh nhân**.

### 2.4. Sơ đồ Tuần tự và State Diagram

**Sơ đồ Tuần tự (Sequence Diagram)** mô tả chi tiết 17 bước tương tác giữa các thành phần:

- POS ↔ OCR Engine
- OCR ↔ Drug Normalizer (chuẩn hóa tên thuốc)
- DDI Engine ↔ Drug Interaction Database
- Inventory ↔ FEFO Algorithm
- Payment ↔ BHYT API

**State Diagram** mô tả vòng đời của mỗi lô thuốc từ lúc nhập kho đến hết hạn, đảm bảo truy xuất nguồn gốc đầy đủ.

### 2.5. Cơ sở dữ liệu

Nhóm em thiết kế **ERD với 15 bảng chính**, trong đó 7 bảng cốt lõi:

1. **THUOC:** Thông tin chi tiết 4.200 sản phẩm
2. **LO_THUOC:** Quản lý theo số lô, hạn sử dụng
3. **DON_HANG:** Lưu vết mọi giao dịch
4. **KHACH_HANG:** CRM với lịch sử mua hàng
5. **NHAN_VIEN:** Quản lý nhân sự và phân quyền
6. **TON_KHO:** Theo dõi real-time
7. **CHUONG_TRINH_KM:** Quản lý khuyến mãi tự động

Tất cả các bảng đều có:

- Primary Key và Foreign Key chặt chẽ
- Audit fields (ngày tạo, người tạo, ngày sửa)
- Index tối ưu cho tìm kiếm nhanh

Em xin mời bạn Tùng trình bày phần triển khai kỹ thuật.

---

## CHƯƠNG 3: TRIỂN KHAI HỆ THỐNG (Bùi Đức Tùng) - 3.5 phút

### 3.1. Công nghệ sử dụng

Xin chào thầy cô, em là Bùi Đức Tùng, phụ trách kiến trúc và triển khai.

Nhóm em lựa chọn **technology stack hiện đại và phù hợp** với quy mô doanh nghiệp:

**Backend:**

- **Spring Boot 3.0** với Java 17 - framework mạnh mẽ, bảo mật cao
- **PostgreSQL 15** - database mã nguồn mở, hỗ trợ JSON, full-text search
- **Redis** - cache tăng tốc độ truy vấn

**Frontend:**

- **React 18** với TypeScript - UI hiện đại, responsive
- **Ant Design** - thư viện component chuẩn doanh nghiệp
- **Redux** - quản lý state phức tạp

**AI & ML:**

- **TensorFlow** cho OCR nhận dạng chữ viết
- **Prophet** (Facebook) cho dự báo nhu cầu theo thời gian

**Cloud & Infrastructure:**

- **AWS** làm nền tảng chính:
  - EC2 cho application server
  - RDS Multi-AZ cho database (high availability)
  - S3 cho lưu trữ hình ảnh, backup
  - CloudFront CDN
  - Lambda cho serverless functions

### 3.2. Kiến trúc Deployment

Nhóm em thiết kế **kiến trúc triển khai 3 lớp** với high availability:

**Layer 1 - Edge Layer:**

- Route 53 DNS
- CloudFront CDN phân phối static assets
- Load Balancer phân tải

**Layer 2 - Application Layer:**

- 2 EC2 instances chạy Spring Boot (Active-Active)
- Auto Scaling tự động tăng giảm theo tải
- Health check liên tục

**Layer 3 - Data Layer:**

- RDS PostgreSQL Multi-AZ (master-slave)
- Redis Cluster 3 nodes
- S3 cho backup hàng ngày
- Automated snapshot mỗi 6 giờ

**Mục tiêu SLA:** 99.9% uptime - chỉ chấp nhận downtime tối đa 43 phút/tháng.

### 3.3. Component Diagram - 8 Module chính

Hệ thống được chia thành **8 microservices độc lập**:

**1. Pharmacy Management Service (Core):**

- Quản lý thuốc, nhà cung cấp
- Xử lý đơn thuốc
- API Gateway cho các service khác

**2. Inventory Service → Giải quyết Vấn đề 1:**

- FEFO algorithm
- Real-time stock tracking
- Auto reorder khi tồn kho < ngưỡng
- SMS/email alert thuốc hết hạn

**3. POS & Sales Service → Giải quyết Vấn đề 2:**

- Bán hàng nhanh với barcode
- Multi-payment gateway
- Hóa đơn điện tử

**4. DDI (Drug-Drug Interaction) Service:**

- Database 50.000+ tương tác thuốc từ FDA, EMA, Bộ Y tế VN
- Real-time checking
- Alert phân cấp 5 mức độ nghiêm trọng

**5. AI/ML Service → Giải quyết Vấn đề 4:**

- OCR Engine nhận dạng đơn thuốc
- Prophet model dự báo nhu cầu
- Seasonal analysis (mùa đông → cảm cúm tăng)

**6. CRM Service → Giải quyết Vấn đề 3:**

- Customer 360° view
- Loyalty points program
- SMS marketing tự động
- Phân tích RFM (Recency, Frequency, Monetary)

**7. HR & Payroll Service → Giải quyết Vấn đề 5:**

- QR code chấm công
- Tính lương tự động
- Quản lý ca làm việc

**8. BI Dashboard Service → Giải quyết Vấn đề 6:**

- Real-time analytics
- Báo cáo doanh thu, lợi nhuận
- ABC/XYZ analysis sản phẩm
- Predictive analytics

### 3.4. Bảo mật và tuân thủ

**Security measures:**

- **Authentication:** JWT token với refresh mechanism
- **Authorization:** Role-Based Access Control (RBAC)
- **Encryption:** AES-256 cho dữ liệu nhạy cảm
- **Audit trail:** Log mọi thao tác quan trọng
- **GDPR compliance:** Quyền xóa dữ liệu, data anonymization

**Tuân thủ quy định Việt Nam:**

- Thông tư 01/2020/TT-BYT về GPP
- Nghị định 13/2023 về bảo vệ dữ liệu cá nhân
- Luật An toàn thông tin mạng 2018

### 3.5. Đạo đức AI trong hệ thống

Đây là phần rất quan trọng vì liên quan đến tính mạng con người.

Nhóm em đã xây dựng **khung đạo đức AI** dựa trên 5 nguyên tắc:

**1. Không gây hại (Non-Maleficence):**

- OCR chỉ hiển thị kết quả nếu confidence ≥ 95%
- Dược sĩ BẮT BUỘC kiểm tra lại trước khi bán
- DDI database cập nhật hàng tháng

**2. Làm điều tốt (Beneficence):**

- AI ưu tiên gợi ý thuốc generic rẻ hơn (tiết kiệm 85K cho khách)
- Không ưu tiên thuốc có margin cao

**3. Quyền tự quyết (Autonomy):**

- Khách hàng có quyền từ chối AI, yêu cầu tư vấn trực tiếp
- Consent rõ ràng khi thu thập dữ liệu

**4. Công bằng (Justice):**

- Không phân biệt đối xử dựa trên khả năng chi trả
- Audit định kỳ phát hiện bias

**5. Giải thích được (Explainability):**

- Mọi khuyến nghị AI phải kèm lý do
- Ví dụ: "Không khuyên thuốc X vì đang dùng thuốc Y, có nguy cơ rối loạn nhịp tim (DDI-2341)"

**Quy trình xử lý sự cố:**

- 0-2 giờ: Tắt tính năng, thông báo khách hàng
- 2-24 giờ: Điều tra, báo cáo Bộ Y tế (nếu nghiêm trọng)
- 1-7 ngày: Fix bug, test kỹ
- 7-30 ngày: Cập nhật quy trình, đào tạo lại

Em xin mời bạn Minh trình bày phần quản lý dự án.

---

## CHƯƠNG 5: QUẢN LÝ DỰ ÁN (Đào Duy Minh) - 3 phút

### 5.1. Kế hoạch triển khai Agile

Cảm ơn bạn Tùng. Em là Đào Duy Minh, phụ trách kế hoạch triển khai và quản lý rủi ro.

Nhóm em đề xuất triển khai trong **12 tháng** theo phương pháp **Agile Scrum**, chia thành 24 sprint (mỗi sprint 2 tuần).

**Giai đoạn 1: Thiết lập nền tảng (Tháng 1-3):**

- Sprint 1-2: Phân tích yêu cầu chi tiết
- Sprint 3-4: Thiết lập infrastructure AWS
- Sprint 5-6: Module Authentication, User Management

**Giai đoạn 2: Phát triển chính (Tháng 4-7):**

- Sprint 7-10: Module Inventory + FEFO
- Sprint 11-12: POS + Payment Gateway
- Sprint 13-14: DDI Engine

**Giai đoạn 3: Tính năng nâng cao (Tháng 8-10):**

- Sprint 15-16: AI OCR + Prophet forecasting
- Sprint 17-18: CRM + Loyalty Program
- Sprint 19-20: Mobile app

**Giai đoạn 4: Kiểm thử và Go-live (Tháng 11-12):**

- Sprint 21-22: UAT với nhân viên thực tế
- Sprint 23: Data migration từ hệ thống cũ
- Sprint 24: Go-live + Hypercare support

### 5.2. Ma trận rủi ro

Nhóm em đã nhận diện **8 rủi ro chính** và biện pháp giảm thiểu:

**RỦI RO 1 - OCR không đủ chính xác (Cao x Cao = Nghiêm trọng):**

- _Biện pháp:_ Train với 10.000+ đơn thật, có manual entry backup, dược sĩ bắt buộc kiểm tra

**RỦI RO 2 - Quy định Bộ Y tế thay đổi (Trung bình x Cao):**

- _Biện pháp:_ Thiết kế linh hoạt, tham vấn luật sư chuyên ngành

**RỦI RO 3 - BHYT API thay đổi (Trung bình x Cao):**

- _Biện pháp:_ Adapter pattern, có offline fallback

**RỦI RO 4 - Nhân viên kháng cự thay đổi (Cao x Trung bình):**

- _Biện pháp:_ Đào tạo kỹ lưỡng, change management, ghi nhận người tiên phong

**RỦI RO 5 - Data migration lỗi (Trung bình x Cao):**

- _Biện pháp:_ Backup đầy đủ, chạy song song 1 tháng

**RỦI RO 6 - Security breach (Thấp x Nghiêm trọng):**

- _Biện pháp:_ Penetration testing, security audit định kỳ

**RỦI RO 7 - Chậm tiến độ (Cao x Cao):**

- _Biện pháp:_ Dự phòng 15% thời gian, có thể outsource module không critical

**RỦI RO 8 - Budget overrun (Trung bình x Trung bình):**

- _Biện pháp:_ Review hàng tháng, scope control chặt chẽ

### 5.3. Kế hoạch đào tạo

**Đào tạo phân theo đối tượng:**

**Dược sĩ (40 giờ):**

- Module 1: Hệ thống cơ bản (4h)
- Module 2: OCR, DDI, tư vấn AI (16h)
- Module 3: CRM, BHYT integration (12h)
- Module 4: Case study thực tế (8h)

**Thủ kho (32 giờ):**

- FEFO algorithm
- Barcode scanning
- Reorder automation
- Báo cáo inventory

**Thu ngân (24 giờ):**

- POS operations
- Multi-payment
- BHYT processing
- Refund handling

**Quản lý (16 giờ):**

- BI Dashboard
- KPI monitoring
- Báo cáo phân tích

**Phương pháp đào tạo:**

- 40% lý thuyết + 60% thực hành
- Sử dụng dữ liệu thật (đã anonymize)
- Mentor 1-1 trong tuần đầu
- Video hướng dẫn để ôn lại

### 5.4. KPI đánh giá thành công

Sau khi triển khai, nhóm em đề xuất theo dõi **4 nhóm KPI:**

**KPI Kinh doanh:**

- Tăng doanh thu: Mục tiêu +15-20% năm đầu
- Tăng giá trị đơn hàng trung bình: +15%
- Customer retention: +20%
- NPS Score: >8/10

**KPI Vận hành:**

- Giảm thời gian phục vụ: 10 phút → 3 phút (-70%)
- Độ chính xác tồn kho: 85% → 99.5%
- Giảm thuốc hết hạn: -50%
- Giảm stockout: -60%

**KPI Kỹ thuật:**

- System uptime: >99.9%
- Response time: <2 giây
- Zero critical security incidents
- Mobile app rating: >4.5/5

**KPI Nhân sự:**

- 100% nhân viên hoàn thành đào tạo
- User satisfaction: >4.0/5
- Adoption rate: >80% sau 3 tháng

Em xin mời trưởng nhóm Năng Ân kết luận.

---

## KẾT LUẬN (Phạm Năng Ân) - 1.5 phút

Cảm ơn các bạn đã trình bày chi tiết.

### Tóm tắt thành tựu

Qua 4 tháng nghiên cứu, nhóm chúng em đã hoàn thành:

**1. Phân tích toàn diện:**

- Khảo sát thực tế tại Long Châu 175 Tây Sơn
- Nhận diện 7 vấn đề cốt lõi gây thiệt hại 33 triệu/6 tháng
- Nghiên cứu 4 đối thủ cạnh tranh (Pharmacity, Guardian, An Khang, Medicare)

**2. Thiết kế hệ thống hoàn chỉnh:**

- 15 sơ đồ UML đầy đủ bằng tiếng Việt
- Kiến trúc 3-tier scalable
- 8 microservices giải quyết từng vấn đề cụ thể

**3. Lựa chọn công nghệ phù hợp:**

- Spring Boot, React, PostgreSQL
- AWS Cloud infrastructure
- AI/ML tích hợp sâu

**4. Kế hoạch triển khai chi tiết:**

- 12 tháng theo Agile
- Quản lý 8 rủi ro chính
- Đào tạo 4 nhóm nhân viên

### Giá trị đóng góp

**Về mặt lý thuyết:**

- Ứng dụng thành công UML trong domain y tế phức tạp
- Đề xuất framework đạo đức AI cho ngành dược
- Nghiên cứu case điển hình chuyển đổi số nhà thuốc

**Về mặt thực tiễn:**

- Giải pháp cụ thể, có thể triển khai ngay
- Tiết kiệm 33 triệu/6 tháng chỉ riêng 1 cơ sở
- Nâng cao chất lượng dịch vụ và an toàn người bệnh
- Có thể nhân rộng cho 1.100+ cơ sở Long Châu

### Hướng phát triển

**Ngắn hạn (6-12 tháng):**

- Pilot tại 175 Tây Sơn
- Thu thập feedback và tinh chỉnh

**Trung hạn (1-3 năm):**

- Mở rộng 500+ cơ sở
- Tích hợp bệnh viện, phòng khám
- Blockchain truy xuất nguồn gốc

**Dài hạn (3-5 năm):**

- Nền tảng chăm sóc sức khỏe tổng thể
- AI dự báo bệnh tật
- Mở rộng ASEAN

### Lời cảm ơn

Nhóm chúng em xin chân thành cảm ơn:

- **Cô Trần Hồng Diệp** - đã tận tình hướng dẫn, góp ý quý báu
- **Khoa Công nghệ Thông tin** - tạo điều kiện học tập tốt nhất
- **Long Châu 175 Tây Sơn** - cung cấp dữ liệu thực tế
- **Các bạn lớp 64HTTT4** - luôn động viên, chia sẻ

Nhóm em hy vọng đề tài này không chỉ là một bài tập lớn mà còn là đóng góp nhỏ bé cho sự nghiệp chuyển đổi số y tế Việt Nam.

**Nhóm em xin chân thành cảm ơn và rất mong nhận được góp ý của thầy cô!**

---

## PHỤ LỤC: CÂU HỎI THƯỜNG GẶP (Q&A)

### Câu hỏi 1: Tại sao chọn AWS thay vì Google Cloud hoặc Azure?

**Trả lời (Bùi Đức Tùng):**

Thưa thầy/cô, nhóm em đã so sánh 3 nền tảng và chọn AWS vì:

1. **Ecosystem phong phú:** AWS có 200+ services, đặc biệt mạnh về healthcare (AWS HealthLake, Amazon Comprehend Medical)
2. **Chi phí tối ưu:** EC2 Reserved Instances tiết kiệm 30-50% so với on-demand
3. **Compliance:** AWS đã được chứng nhận HIPAA, GDPR phù hợp ngành y tế
4. **Community lớn:** Nhiều tài liệu, dễ tìm nhân sự có kinh nghiệm AWS tại VN
5. **FPT là AWS Partner:** Long Châu thuộc FPT Retail → có hỗ trợ từ FPT Cloud

### Câu hỏi 2: Làm sao đảm bảo độ chính xác OCR 95%?

**Trả lời (Nguyễn Bảo Tuấn):**

Thưa thầy/cô, để đạt 95% accuracy, nhóm em áp dụng:

1. **Training data lớn:** 10.000+ đơn thuốc thật từ nhiều bác sĩ, nhiều kiểu chữ
2. **Data augmentation:** Xoay, nghiêng, làm mờ để model robust hơn
3. **Ensemble model:** Kết hợp TensorFlow OCR + Tesseract + Google Vision API → vote kết quả
4. **Confidence threshold:** Chỉ hiển thị nếu ≥95%, dưới 95% → yêu cầu nhập tay
5. **Human-in-the-loop:** Dược sĩ BẮT BUỘC kiểm tra trước khi bán
6. **Feedback loop:** Lưu lại những trường hợp sai để retrain model

Quan trọng nhất: **An toàn > Tiện lợi**. Khi không chắc chắn, hệ thống sẽ yêu cầu con người quyết định.

### Câu hỏi 3: Nếu hệ thống bị sập thì sao? Nhà thuốc có bán được hàng không?

**Trả lời (Bùi Đức Tùng):**

Thưa thầy/cô, nhóm em có 3 tầng phòng thủ:

**Tầng 1 - High Availability:**

- RDS Multi-AZ tự động failover trong 60 giây
- 2 EC2 instances Active-Active
- Load Balancer health check mỗi 30 giây

**Tầng 2 - Offline Mode:**

- POS có database local SQLite
- Khi mất kết nối internet → chuyển offline mode
- Vẫn bán hàng được, sync lại khi có mạng

**Tầng 3 - Manual Backup:**

- Có quy trình bán hàng thủ công dự phòng
- In ra danh sách thuốc bán chạy + giá
- Ghi tay vào sổ, nhập lại sau

**Cam kết SLA 99.9%** = downtime tối đa 43 phút/tháng, đủ để xử lý sự cố.

### Câu hỏi 4: Chi phí 3.8 tỷ VNĐ có quá cao cho 1 cơ sở nhỏ?

**Trả lời (Hoàng Văn Cường):**

Thưa thầy/cô, thực ra con số 3.8 tỷ là cho **phát triển hệ thống trung tâm**, sau đó sẽ nhân rộng cho 1.100+ cơ sở.

**Chi phí phân bổ cho từng cơ sở chỉ ~3.5 triệu VNĐ**, bao gồm:

- 1 máy POS: 2 triệu
- 1 barcode scanner: 0.5 triệu
- 1 máy in hóa đơn: 1 triệu

**Chi phí vận hành/tháng chỉ 137K VNĐ/cơ sở** (1.644 triệu / 12 tháng / 1.100 cơ sở).

**So sánh lợi ích:**

- Tiết kiệm 33 triệu/6 tháng = 5.5 triệu/tháng
- Chi phí vận hành: 137K/tháng
- **Lợi nhuận ròng: 5.4 triệu/tháng/cơ sở**

ROI là 72.8%, payback chỉ 3.2 năm, **rất khả thi**.

### Câu hỏi 5: Làm sao đảm bảo nhân viên không kháng cự thay đổi?

**Trả lời (Đào Duy Minh):**

Thưa thầy/cô, đây là rủi ro lớn nhất! Nhóm em áp dụng **Change Management 8 bước của Kotter:**

**Bước 1-2: Tạo cảm giác cấp thiết**

- Trình bày 7 vấn đề, thiệt hại 33 triệu
- Khách hàng phàn nàn về tốc độ chậm

**Bước 3-4: Xây liên minh dẫn dắt**

- Chọn 2-3 dược sĩ "champion" tham gia từ đầu
- Họ sẽ thuyết phục đồng nghiệp

**Bước 5-6: Đào tạo kỹ lưỡng**

- 40 giờ cho dược sĩ, không chỉ "bấm nút"
- Giải thích TẠI SAO cần thay đổi, KHÔNG CHỈ CÁI GÌ thay đổi

**Bước 7: Ghi nhận chiến thắng nhanh**

- Tuần đầu: Tặng thưởng cho người dùng tích cực nhất
- Tháng đầu: Tổ chức workshop chia sẻ kinh nghiệm

**Bước 8: Củng cố văn hóa**

- Đưa "sử dụng hệ thống thành thạo" vào KPI đánh giá
- Khen thưởng công khai

**Kinh nghiệm từ thực tế:** Pharmacity triển khai hệ thống tương tự năm 2020, ban đầu 30% nhân viên kháng cự, sau 3 tháng chỉ còn 5%.

---

**HẾT - CHÚC THẦY CÔ VÀ CÁC BẠN BUỔI HỌC VUI VẺ!** 🎓
