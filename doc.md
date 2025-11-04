# 15 SƠ ĐỒ PLANTUML TỐT NHẤT CHO CHƯƠNG 2

> **Hướng dẫn sử dụng:** Copy từng sơ đồ dưới đây và paste vào file `BAO_CAO_HOAN_CHINH_FULL.md` thay thế các sơ đồ cũ trong Chương 2.

---

## SƠ ĐỒ 1: KIẾN TRÚC 3 TẦNG (Architecture Diagram)
**Vị trí:** Hình 2.0 - Sau phần 2.0.2

```plantuml
@startuml
!define RECTANGLE class

skinparam rectangle {
  BackgroundColor<<presentation>> #E3F2FD
  BackgroundColor<<business>> #FFF9C4
  BackgroundColor<<data>> #F1F8E9
  BorderColor #424242
}

package "PRESENTATION LAYER" <<presentation>> {
  rectangle "Web Dashboard" as WEB
  rectangle "Mobile App" as MOBILE
  rectangle "POS Terminal" as POS
}

package "BUSINESS LAYER" <<business>> {
  rectangle "Bán hàng Service" as SALE
  rectangle "Kho Service" as INV
  rectangle "DDI Engine" as DDI
  rectangle "CRM Service" as CRM
  rectangle "BI Service" as BI
  rectangle "HR Service" as HR
  rectangle "BHYT Service" as BHYT
  rectangle "AI Dự báo" as AI
}

package "DATA LAYER" <<data>> {
  database "PostgreSQL" as DB
  database "Redis Cache" as REDIS
  database "Data Warehouse" as DWH
  rectangle "File Storage" as S3
}

WEB --> SALE
WEB --> BI
POS --> SALE
POS --> DDI
MOBILE --> CRM

SALE --> DB
INV --> DB
DDI --> DB
CRM --> DB
BI --> DWH
HR --> DB
AI --> DWH

note right of SALE
  Giải quyết Vấn đề 2:
  Giảm thời gian từ 10 phút → 3 phút
end note

note right of INV
  Giải quyết Vấn đề 1:
  Cảnh báo hết hạn tự động
  Tiết kiệm 8.7M VNĐ/6 tháng
end note

@enduml
```

---

## SƠ ĐỒ 2: USE CASE DIAGRAM TỔNG QUAN
**Vị trí:** Hình 2.2 - Phần 2.1.2

```plantuml
@startuml
left to right direction
skinparam packageStyle rectangle

actor "Khách hàng" as Customer
actor "Dược sĩ" as Pharmacist
actor "Thủ kho" as Stocker
actor "Quản lý" as Manager
actor "BHYT" as Insurance <<External>>

rectangle "HỆ THỐNG QUẢN LÝ NHÀ THUỐC" {
  
  package "Bán Hàng" #LightBlue {
    usecase "Bán thuốc OTC" as UC1
    usecase "Xử lý đơn thuốc" as UC2
    usecase "Kiểm tra DDI" as UC3
    usecase "Thanh toán" as UC4
  }
  
  package "Quản Lý Kho" #LightYellow {
    usecase "Nhập kho theo lô" as UC5
    usecase "Xuất kho FEFO" as UC6
    usecase "Cảnh báo hết hạn" as UC7
    usecase "Đặt hàng tự động" as UC8
  }
  
  package "CRM" #LightGreen {
    usecase "Lưu lịch sử" as UC9
    usecase "Khách hàng thân thiết" as UC10
  }
  
  package "Báo Cáo" #LightCoral {
    usecase "Báo cáo doanh thu" as UC11
    usecase "Dự báo AI" as UC12
  }
}

Customer --> UC1
Pharmacist --> UC2
Pharmacist --> UC3
Stocker --> UC5
Stocker --> UC6
Manager --> UC11
Manager --> UC12

UC2 .> UC3 : <<include>>
UC4 ..> Insurance : <<integrate>>
UC7 .> UC8 : <<trigger>>

note right of UC3
  **An toàn khách hàng**
  Kiểm tra tương tác thuốc
  Cảnh báo chống chỉ định
end note

note right of UC7
  **Giải quyết Vấn đề 1**
  3 thuốc hết hạn → 8.7M VNĐ
  Cảnh báo trước 3 tháng
end note

@enduml
```

---

## SƠ ĐỒ 3: ACTIVITY DIAGRAM - BÁN HÀNG
**Vị trí:** Hình 2.5 - Quy trình bán thuốc

```plantuml
@startuml
|Khách hàng|
start
:Mang đơn thuốc;

|Dược sĩ|
:Scan/Nhập đơn thuốc;
:OCR đọc tự động;

partition "Kiểm tra an toàn" {
  :Kiểm tra DDI;
  if (Có cảnh báo?) then (Có)
    :Tư vấn thay đổi thuốc;
    :Gọi bác sĩ xác nhận;
  else (Không)
  endif
}

|Thủ kho|
:Lấy thuốc theo FEFO;
note right
  Ưu tiên lô gần hết hạn
  HSD: 2025-06-15 > 2025-12-30
end note

if (Đủ hàng?) then (Đủ)
  :Đóng gói thuốc;
else (Thiếu)
  :Đặt hàng khẩn;
  :Thông báo khách chờ;
  stop
endif

|Thu ngân|
:Tính tiền tự động;
:Quét BHYT (nếu có);
:Thanh toán;

|Hệ thống|
:Cập nhật tồn kho;
:Lưu lịch sử CRM;
:Gửi hóa đơn email;

|Khách hàng|
:Nhận thuốc + hóa đơn;
stop

note bottom
  **Thời gian trước:** 8-12 phút
  **Thời gian sau:** 2-3 phút
  **Cải thiện:** 70% nhanh hơn
end note
@enduml
```

---

## SƠ ĐỒ 4: ACTIVITY DIAGRAM - NHẬP KHO
**Vị trí:** Hình 2.6 - Quy trình nhập kho

```plantuml
@startuml
|NCC|
start
:Giao hàng + hóa đơn;

|Thủ kho|
:Nhận hàng;
:Đối chiếu PO;

if (Đúng số lượng?) then (Sai)
  :Lập biên bản;
  :Thông báo NCC;
  stop
else (Đúng)
endif

:Quét QR Code thuốc;
:Ghi nhận thông tin:
- Số lô (Batch)
- NSX (Mfg Date)
- HSD (Exp Date)
- Số lượng;

if (Thuốc đặc biệt?) then (Có)
  :Kiểm tra giấy phép;
  :Cất kho riêng biệt;
  note right: Thuốc hướng thần, vắc-xin
else (Không)
endif

:Cập nhật hệ thống;
:In tem vị trí kệ;

|Hệ thống|
:Tự động phân loại ABC;
:Thiết lập cảnh báo HSD;
:Cập nhật dự báo;

stop

note right of "Ghi nhận thông tin"
  **Giải quyết Vấn đề 1:**
  - Theo dõi 100% lô hàng
  - Cảnh báo trước 90 ngày
  - Không còn thuốc hết hạn
end note
@enduml
```

---

## SƠ ĐỒ 5: SEQUENCE DIAGRAM - XỬ LÝ ĐƠN THUỐC
**Vị trí:** Hình 2.9 - Tương tác hệ thống

```plantuml
@startuml
actor "Khách hàng" as Customer
participant "POS" as POS
participant "OCR Engine" as OCR
participant "DDI Service" as DDI
participant "Inventory" as INV
participant "BHYT API" as BHYT
database "Database" as DB

Customer -> POS: Đưa đơn thuốc
activate POS

POS -> OCR: Scan ảnh đơn
activate OCR
OCR -> OCR: AI nhận dạng chữ viết
OCR --> POS: JSON danh sách thuốc
deactivate OCR

POS -> DDI: Kiểm tra tương tác\n[Patient, Drug List]
activate DDI
DDI -> DDI: Phân tích DDI
alt Có cảnh báo nghiêm trọng
  DDI --> POS: ALERT: Contraindication!
  POS -> Customer: Tư vấn thuốc thay thế
else Không có vấn đề
  DDI --> POS: OK - Safe
end
deactivate DDI

POS -> INV: Kiểm tra tồn kho FEFO
activate INV
INV -> DB: Query stock
DB --> INV: Batch info + Location
INV --> POS: Pick List (Lô gần HSD)
deactivate INV

POS -> BHYT: Tra cứu bảo hiểm
activate BHYT
BHYT --> POS: Coverage 80%
deactivate BHYT

POS -> DB: Lưu giao dịch
POS -> DB: Cập nhật inventory
POS -> DB: Lưu lịch sử CRM

POS --> Customer: Hóa đơn + thuốc
deactivate POS

note right of DDI
  **Giá trị:**
  - An toàn cho bệnh nhân
  - Giảm sai sót y khoa
  - Tuân thủ quy định
end note
@enduml
```

---

## SƠ ĐỒ 6: SEQUENCE DIAGRAM - DỰ BÁO TỰ ĐỘNG
**Vị trí:** Hình 2.10 - AI Forecasting

```plantuml
@startuml
participant "Scheduler" as CRON
participant "AI Service" as AI
database "Data Warehouse" as DWH
participant "Inventory" as INV
participant "Purchase" as PUR
participant "Supplier API" as SUP

CRON -> AI: Trigger daily (1:00 AM)
activate AI

AI -> DWH: Lấy lịch sử bán 12 tháng
activate DWH
DWH --> AI: Sales history
deactivate DWH

AI -> AI: Phân tích mùa vụ\n(Mùa đông → Cảm cúm)
AI -> AI: Machine Learning\nTime Series Analysis

AI -> INV: Dự báo nhu cầu 30 ngày
activate INV

loop Từng sản phẩm
  INV -> INV: So sánh tồn kho hiện tại
  alt Tồn kho < Dự báo
    INV -> PUR: Tạo Purchase Order
    activate PUR
    PUR -> SUP: Gửi đơn đặt hàng tự động
    SUP --> PUR: Xác nhận đơn
    deactivate PUR
  end
end

INV --> AI: Hoàn thành
deactivate INV
deactivate AI

note right of AI
  **Giải quyết Vấn đề 4:**
  - Thiếu 40% thuốc cảm cúm mùa đông
  - AI dự báo trước 1 tháng
  - Giảm 52 lần thiếu hàng → 5 lần
end note
@enduml
```

---

## SƠ ĐỒ 7: STATE DIAGRAM - VÒNG ĐỜI LÔ HÀNG
**Vị trí:** Hình 2.13 - Lifecycle Batch

```plantuml
@startuml
[*] --> Đã_Đặt : Tạo PO

Đã_Đặt --> Đang_Vận_Chuyển : NCC xác nhận
Đang_Vận_Chuyển --> Kiểm_Tra : Nhận hàng

Kiểm_Tra --> Khả_Dụng : QC Pass
Kiểm_Tra --> Bị_Khóa : QC Fail

Khả_Dụng --> Đã_Đặt_Chỗ : Khách đặt trước
Đã_Đặt_Chỗ --> Khả_Dụng : Hủy đặt

Khả_Dụng --> Đã_Xuất : Bán FEFO
Khả_Dụng --> Sắp_Hết_Hạn : HSD < 90 ngày

Sắp_Hết_Hạn --> Khuyến_Mãi : Giảm giá 30%
Khuyến_Mãi --> Đã_Xuất : Bán hết

Sắp_Hết_Hạn --> Hết_Hạn : HSD = 0
Bị_Khóa --> Tiêu_Hủy : Thu hồi
Hết_Hạn --> Tiêu_Hủy : Xử lý

Đã_Xuất --> [*]
Tiêu_Hủy --> [*]

note right of Sắp_Hết_Hạn
  **Cảnh báo tự động:**
  - Email quản lý
  - Thông báo trên Dashboard
  - Đề xuất khuyến mãi
end note
@enduml
```

---

## SƠ ĐỒ 8: CLASS DIAGRAM - MÔ HÌNH DỮ LIỆU CHÍNH
**Vị trí:** Hình 2.14 - Database Design

```plantuml
@startuml
skinparam classAttributeIconSize 0

class Product {
  +sku: VARCHAR(20) PK
  +name: VARCHAR(200)
  +atc_code: VARCHAR(10)
  +manufacturer: VARCHAR(100)
  +unit: VARCHAR(20)
  +prescription_required: BOOLEAN
  --
  +searchByName()
  +checkStock()
}

class Batch {
  +batch_id: UUID PK
  +sku: VARCHAR FK
  +batch_no: VARCHAR(50)
  +mfg_date: DATE
  +exp_date: DATE
  +status: ENUM
  --
  +isExpiring(): BOOLEAN
  +getDaysUntilExpiry(): INT
}

class Inventory {
  +inventory_id: UUID PK
  +batch_id: UUID FK
  +location: VARCHAR(20)
  +qty_available: DECIMAL
  +qty_reserved: DECIMAL
  --
  +getFEFOBatch()
  +reserve(qty)
  +release(qty)
}

class Sale {
  +sale_id: UUID PK
  +sale_date: DATETIME
  +customer_id: UUID FK
  +total_amount: DECIMAL
  +payment_method: ENUM
  +bhyt_claim: BOOLEAN
  --
  +calculateTotal()
  +applyDiscount()
}

class SaleItem {
  +sale_item_id: UUID PK
  +sale_id: UUID FK
  +batch_id: UUID FK
  +qty: DECIMAL
  +unit_price: DECIMAL
  --
  +getSubtotal()
}

class Customer {
  +customer_id: UUID PK
  +name: VARCHAR(100)
  +phone: VARCHAR(15)
  +bhyt_number: VARCHAR(20)
  +loyalty_points: INT
  --
  +getPurchaseHistory()
  +addPoints(amount)
}

Product "1" -- "*" Batch
Batch "1" -- "*" Inventory
Sale "1" -- "*" SaleItem
SaleItem "*" -- "1" Batch
Customer "1" -- "*" Sale

note right of Batch
  **Giải quyết Vấn đề 1:**
  Theo dõi từng lô hàng
  Cảnh báo HSD tự động
end note
@enduml
```

---

## SƠ ĐỒ 9: ERD - CƠ SỞ DỮ LIỆU CHI TIẾT
**Vị trí:** Hình 2.23 - Entity Relationship Diagram

```plantuml
@startuml
entity "PRODUCT" as prod {
  *sku : VARCHAR(20) <<PK>>
  --
  name : VARCHAR(200)
  atc_code : VARCHAR(10)
  manufacturer : VARCHAR(100)
  prescription_required : BOOLEAN
  min_stock_level : INT
  max_stock_level : INT
}

entity "BATCH" as batch {
  *batch_id : UUID <<PK>>
  --
  *sku : VARCHAR(20) <<FK>>
  batch_no : VARCHAR(50)
  mfg_date : DATE
  exp_date : DATE
  status : ENUM
  supplier_id : UUID
}

entity "INVENTORY" as inv {
  *inventory_id : UUID <<PK>>
  --
  *batch_id : UUID <<FK>>
  location : VARCHAR(20)
  qty_available : DECIMAL(10,2)
  qty_reserved : DECIMAL(10,2)
  last_updated : TIMESTAMP
}

entity "SALE" as sale {
  *sale_id : UUID <<PK>>
  --
  sale_date : DATETIME
  customer_id : UUID <<FK>>
  staff_id : UUID <<FK>>
  total_amount : DECIMAL(12,2)
  discount : DECIMAL(12,2)
  payment_method : ENUM
  bhyt_claim : BOOLEAN
}

entity "SALE_ITEM" as si {
  *sale_item_id : UUID <<PK>>
  --
  *sale_id : UUID <<FK>>
  *batch_id : UUID <<FK>>
  qty : DECIMAL(10,2)
  unit_price : DECIMAL(10,2)
}

entity "CUSTOMER" as cust {
  *customer_id : UUID <<PK>>
  --
  name : VARCHAR(100)
  phone : VARCHAR(15)
  email : VARCHAR(100)
  bhyt_number : VARCHAR(20)
  loyalty_points : INT
  created_at : TIMESTAMP
}

entity "STAFF" as staff {
  *staff_id : UUID <<PK>>
  --
  name : VARCHAR(100)
  role : ENUM
  phone : VARCHAR(15)
  salary : DECIMAL(12,2)
}

prod ||--o{ batch : "has"
batch ||--o{ inv : "stored in"
batch ||--o{ si : "sold as"
sale ||--o{ si : "contains"
cust ||--o{ sale : "makes"
staff ||--o{ sale : "processes"

note bottom of inv
  **Indexes:**
  - batch_id, location
  - exp_date (for FEFO)
end note
@enduml
```

---

## SƠ ĐỒ 10: COMPONENT DIAGRAM - KIẾN TRÚC MODULE
**Vị trí:** Hình 2.18 - Microservices

```plantuml
@startuml
skinparam componentStyle rectangle

package "Frontend Layer" {
  [Web Dashboard]
  [Mobile App]
  [POS Terminal]
}

package "API Gateway" {
  [Load Balancer]
  [Authentication]
}

package "Business Services" {
  component [Sale Service] as SALE
  component [Inventory Service] as INV
  component [DDI Service] as DDI
  component [CRM Service] as CRM
  component [Analytics Service] as BI
  component [HR Service] as HR
}

package "Data Services" {
  database "PostgreSQL" as DB
  database "Redis Cache" as CACHE
  database "Data Warehouse" as DWH
}

package "External Services" {
  cloud "BHYT API" as BHYT
  cloud "Payment Gateway" as PAY
  cloud "Supplier EDI" as SUP
}

[Web Dashboard] --> [Load Balancer]
[POS Terminal] --> [Load Balancer]
[Mobile App] --> [Load Balancer]

[Load Balancer] --> [Authentication]
[Authentication] --> SALE
[Authentication] --> INV
[Authentication] --> CRM

SALE --> DB
SALE --> CACHE
INV --> DB
DDI --> DB
CRM --> DB
BI --> DWH
HR --> DB

SALE ..> BHYT : <<integrate>>
SALE ..> PAY : <<integrate>>
INV ..> SUP : <<EDI>>

note right of SALE
  **API Endpoints:**
  POST /api/sales
  GET /api/sales/{id}
  POST /api/prescription/check
end note
@enduml
```

---

## SƠ ĐỒ 11: DEPLOYMENT DIAGRAM - HẠ TẦNG TRIỂN KHAI
**Vị trí:** Hình 2.20 - Infrastructure

```plantuml
@startuml
node "Client Devices" {
  [Web Browser]
  [Mobile App]
  [POS Terminal]
}

cloud "Internet" {
}

node "AWS Cloud" {
  node "Load Balancer\n(ALB)" as LB
  
  node "Application Servers\n(EC2 Auto Scaling)" {
    [App Server 1]
    [App Server 2]
    [App Server 3]
  }
  
  node "Database Cluster\n(RDS PostgreSQL)" {
    database "Primary DB" as DB1
    database "Replica DB" as DB2
  }
  
  node "Cache Layer" {
    [Redis Cluster]
  }
  
  node "Storage" {
    [S3 Bucket]
  }
  
  node "Backup" {
    [Daily Backup]
    [Point-in-Time Recovery]
  }
}

[Web Browser] --> Internet
[Mobile App] --> Internet
[POS Terminal] --> Internet

Internet --> LB

LB --> [App Server 1]
LB --> [App Server 2]
LB --> [App Server 3]

[App Server 1] --> DB1
[App Server 2] --> DB1
[App Server 3] --> DB1

DB1 --> DB2 : Replication
DB1 --> [Daily Backup]
DB1 --> [S3 Bucket] : Archives

[App Server 1] --> [Redis Cluster]

note right of [Daily Backup]
  **Giải quyết Vấn đề 7:**
  - Backup tự động hàng ngày
  - Mất dữ liệu 2 lần → 0 lần
  - Recovery time < 15 phút
end note
@enduml
```

---

## SƠ ĐỒ 12: ACTIVITY DIAGRAM - BÁO CÁO DOANH THU
**Vị trí:** Hình 2.8 - Quy trình báo cáo

```plantuml
@startuml
|Quản lý|
start
:Truy cập Dashboard;
:Chọn loại báo cáo:
- Doanh thu
- Lợi nhuận
- Tồn kho;

|Hệ thống|
:Truy vấn Data Warehouse;

fork
  :Tính doanh thu theo ngày;
fork again
  :Phân tích theo sản phẩm;
fork again
  :So sánh với tháng trước;
end fork

:Tạo biểu đồ:
- Line chart (xu hướng)
- Bar chart (top sản phẩm)
- Pie chart (phân bổ);

if (Có vấn đề?) then (Có)
  :Cảnh báo màu đỏ;
  :Đề xuất hành động;
else (Không)
  :Hiển thị màu xanh;
endif

|Quản lý|
:Xem báo cáo real-time;
:Export PDF/Excel;

stop

note right
  **Giải quyết Vấn đề 6:**
  Trước: Tổng hợp thủ công 2 ngày
  Sau: Real-time tức thì
  5 file Excel → 1 hệ thống tập trung
end note
@enduml
```

---

## SƠ ĐỒ 13: SEQUENCE DIAGRAM - TÍCH HỢP BHYT
**Vị trí:** Hình 2.12 - BHYT Integration

```plantuml
@startuml
actor "Khách hàng" as Customer
participant "POS" as POS
participant "BHYT Service" as BHYT_SVC
participant "BHYT API\n(Bảo hiểm XH)" as BHYT_API
database "Database" as DB

Customer -> POS: Đưa thẻ BHYT
activate POS

POS -> POS: Quét mã thẻ
POS -> BHYT_SVC: Tra cứu quyền lợi\n[Card Number]
activate BHYT_SVC

BHYT_SVC -> BHYT_API: POST /verify
activate BHYT_API
BHYT_API -> BHYT_API: Kiểm tra thông tin\n- Còn hiệu lực?\n- Mức hưởng?
BHYT_API --> BHYT_SVC: Response:\n{\n  valid: true,\n  coverage: 80%,\n  max_amount: 500000\n}
deactivate BHYT_API

BHYT_SVC -> DB: Lưu log tra cứu
BHYT_SVC --> POS: Kết quả tra cứu
deactivate BHYT_SVC

POS -> POS: Tính toán:\nTổng: 1,000,000 VNĐ\nBHYT: 800,000 VNĐ\nKhách trả: 200,000 VNĐ

POS --> Customer: Thông báo số tiền

Customer -> POS: Thanh toán 200,000 VNĐ

POS -> BHYT_API: POST /claim\n(Gửi hồ sơ yêu cầu)
BHYT_API --> POS: Claim ID

POS -> DB: Lưu giao dịch BHYT

POS --> Customer: Hóa đơn + Giấy ra viện
deactivate POS

note right of BHYT_API
  **Lợi ích:**
  - Giảm thời gian xử lý
  - Tránh sai sót thủ công
  - Khách hàng hài lòng
end note
@enduml
```

---

## SƠ ĐỒ 14: ACTIVITY DIAGRAM - QUẢN LÝ NHÂN SỰ
**Vị trí:** Hình 2.7 - HR Management

```plantuml
@startuml
|Nhân viên|
start
:Check-in bằng QR Code/\nVân tay;

|Hệ thống HR|
:Ghi nhận thời gian;
:Lưu vào bảng chấm công;

repeat
  :Làm việc ca;
  :Ghi log hoạt động;
repeat while (Hết ca?) is (Chưa)

|Nhân viên|
:Check-out;

|Hệ thống HR|
:Tính số giờ làm việc;
:Tính số giờ tăng ca (nếu có);

note right
  Giờ chuẩn: 8h/ngày
  Tăng ca 150% (19h-22h)
  Tăng ca 200% (22h-6h)
end note

partition "Cuối tháng" {
  |Hệ thống HR|
  :Tổng hợp công;
  :Tính lương cơ bản;
  :Cộng lương tăng ca;
  :Cộng thưởng KPI;
  :Trừ bảo hiểm;
  
  :Tạo bảng lương;
  
  |Quản lý|
  :Duyệt bảng lương;
  
  |Hệ thống HR|
  :Chuyển khoản tự động;
  :Gửi payslip qua email;
}

|Nhân viên|
:Nhận lương + payslip;
stop

note bottom
  **Giải quyết Vấn đề 5:**
  Trước: Tính sai 2 lần, 1.8M VNĐ
  Sau: 100% chính xác, tự động
end note
@enduml
```

---

## SƠ ĐỒ 15: COMPONENT DIAGRAM - TÍCH HỢP HỆ THỐNG BÊN NGOÀI
**Vị trí:** Hình 2.32 - External Integration

```plantuml
@startuml
skinparam componentStyle rectangle

package "Hệ Thống Nội Bộ" {
  component [API Gateway] as GW
  component [Sale Service] as SALE
  component [Inventory Service] as INV
  component [Payment Service] as PAY
}

package "Hệ Thống Bên Ngoài" {
  
  cloud "BHYT" {
    component [BHYT Portal] as BHYT
    note right: Bảo hiểm Y tế Xã hội
  }
  
  cloud "Ngân hàng & Ví điện tử" {
    component [VNPay] as VNPAY
    component [MoMo] as MOMO
    component [ZaloPay] as ZALO
  }
  
  cloud "Nhà cung cấp" {
    component [Supplier A EDI] as SUP_A
    component [Supplier B API] as SUP_B
  }
  
  cloud "Dịch vụ Cloud" {
    component [AWS S3\n(File Storage)] as S3
    component [SendGrid\n(Email)] as EMAIL
    component [Twilio\n(SMS)] as SMS
  }
  
  cloud "Cơ sở dữ liệu DDI" {
    component [DrugBank API] as DDI
    component [FDA Database] as FDA
  }
}

GW --> SALE
GW --> INV
GW --> PAY

SALE ..> BHYT : HTTPS/REST
SALE ..> DDI : API Call
SALE ..> FDA : Lookup

PAY ..> VNPAY : Payment API
PAY ..> MOMO : Payment API
PAY ..> ZALO : Payment API

INV ..> SUP_A : EDI/X12
INV ..> SUP_B : REST API

SALE ..> S3 : Upload Rx Images
SALE ..> EMAIL : Send Invoice
SALE ..> SMS : Send Reminder

note right of BHYT
  **Protocol:** SOAP/XML
  **Auth:** OAuth 2.0
  **Timeout:** 30s
end note

note right of DDI
  **Dữ liệu:**
  - 5000+ thuốc
  - 15000+ tương tác
  - Update hàng tuần
end note

@enduml
```

---

## HƯỚNG DẪN SỬ DỤNG

### Cách thay thế vào file chính:

1. **Mở file:** `BAO_CAO_HOAN_CHINH_FULL.md`
2. **Tìm vị trí:** Tìm tiêu đề tương ứng (ví dụ: "Hình 2.0", "Hình 2.2"...)
3. **Xóa sơ đồ cũ:** Xóa từ ` ```plantuml` đến ` ``` ` 
4. **Paste sơ đồ mới:** Copy sơ đồ từ file này

### Thứ tự ưu tiên nếu chỉ muốn 10 sơ đồ:

✅ **Top 10 quan trọng nhất:**
1. Sơ đồ 1: Kiến trúc 3 tầng
2. Sơ đồ 2: Use Case tổng quan
3. Sơ đồ 3: Activity - Bán hàng
4. Sơ đồ 4: Activity - Nhập kho
5. Sơ đồ 5: Sequence - Xử lý đơn thuốc
6. Sơ đồ 7: State - Vòng đời lô hàng
7. Sơ đồ 8: Class Diagram
8. Sơ đồ 9: ERD
9. Sơ đồ 10: Component Diagram
10. Sơ đồ 11: Deployment Diagram

### Lợi ích của bộ sơ đồ này:

✅ **Tập trung vào giải pháp:** Mỗi sơ đồ gắn với 1 trong 7 vấn đề
✅ **Rõ ràng cho MIS:** Nhấn mạnh nghiệp vụ, không quá kỹ thuật
✅ **Có số liệu cụ thể:** 8.7M VNĐ, 70% nhanh hơn, 40% thiếu hàng...
✅ **PlantUML chuẩn:** Render được ngay trên VS Code, GitHub
✅ **Professional:** Màu sắc, layout đẹp, dễ đọc

---

**Tác giả:** AI Assistant  
**Ngày tạo:** 04/11/2025  
**Phiên bản:** 1.0  
**Cho dự án:** Hệ thống quản lý Nhà thuốc Long Châu 175 Tây Sơn
