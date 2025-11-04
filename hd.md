# 📊 SLIDE THUYẾT TRÌNH - HỆ THỐNG QUẢN LÝ NHÀ THUỐC LONG CHÂU

> **Format:** PowerPoint / Google Slides
> **Thời gian:** 15 phút
> **Số slide:** 9 slides (Tập trung VẤN ĐỀ - GIẢI PHÁP - THIẾT KẾ)
> **Không có phần Tài chính ROI**

---

## SLIDE 1: TRANG BÌA

```
┌─────────────────────────────────────────────┐
│                                             │
│   HỆ THỐNG QUẢN LÝ NHÀ THUỐC LONG CHÂU     │
│         CƠ SỞ 175 TÂY SƠN                   │
│                                             │
│   Đề tài: Phân tích và Thiết kế Hệ thống   │
│   Quản lý Nhà thuốc ứng dụng AI & IoT      │
│                                             │
│   Môn học: Quản trị Hệ thống Thông tin     │
│   Giảng viên: ThS. Trần Hồng Diệp          │
│                                             │
│   Nhóm 3 - Lớp 64HTTT4                     │
│   Trường Đại học Thủy lợi                  │
│   Tháng 12/2024                            │
└─────────────────────────────────────────────┘
```

**Hình ảnh:** Logo trường + Logo Long Châu

---

## SLIDE 2: THÀNH VIÊN NHÓM

```
┌─────────────────────────────────────────────┐
│         THÀNH VIÊN NHÓM THỰC HIỆN          │
├─────────────────────────────────────────────┤
│                                             │
│  1. Phạm Năng Ân        - Trưởng nhóm      │
│     Phần: Vấn đề & Giải pháp               │
│                                             │
│  2. Nguyễn Bảo Tuấn     - Thành viên       │
│     Phần: Phân tích nghiệp vụ              │
│                                             │
│  3. Bùi Đức Tùng        - Thành viên       │
│     Phần: Thiết kế hệ thống                │
│                                             │
│  4. Phan Văn Định       - Thành viên       │
│     Phần: Công nghệ & Triển khai           │
│                                             │
│  5. Đào Duy Minh        - Thành viên       │
│     Phần: Quản lý dự án & KPI              │
└─────────────────────────────────────────────┘
```

---

## SLIDE 3: 7 VẤN ĐỀ CHÍNH (Phạm Năng Ân - 2 phút)

```
┌─────────────────────────────────────────────┐
│    LONG CHÂU 175 TÂY SƠN - 7 VẤN ĐỀ       │
├─────────────────────────────────────────────┤
│                                             │
│  📍 CƠ SỞ NGHIÊN CỨU                       │
│     • 175 Tây Sơn, Hà Nội (gần BV Bạch Mai)│
│     • 120m², 4,200 SKU, 800-1,200 khách/ngày│
│     • Doanh thu: 650-750M VNĐ/tháng        │
│                                             │
│  ⚠️  7 VẤN ĐỀ CHÍNH                        │
│  1️⃣  Quản lý kho kém → 27.9M VNĐ          │
│       • Thuốc hết hạn: 3 lần/6 tháng       │
│       • Kiểm kê thủ công: 8 giờ/lần        │
│                                             │
│  2️⃣  Bán hàng chậm → 8-12 phút/khách      │
│       • Đọc đơn thuốc: thủ công            │
│       • Tìm thuốc: không có hệ thống       │
│                                             │
│  3️⃣  CRM yếu → Mất 15-20% khách           │
│       • Không lưu lịch sử mua              │
│       • Không có loyalty program           │
│                                             │
│  4️⃣  Dự báo kém → Thiếu hàng 40% mùa đông │
│       • Dựa vào kinh nghiệm                │
│       • Không có AI/ML hỗ trợ              │
│                                             │
│  5️⃣  HR thủ công → Sai lương 1.8M         │
│  6️⃣  Dữ liệu rời → 5 file Excel riêng rẽ  │
│  7️⃣  Hạ tầng yếu → Mất data 2 lần         │
│                                             │
│  💰 TỔNG THIỆT HẠI: 33M VNĐ/6 tháng       │
└─────────────────────────────────────────────┘
```

**Hình ảnh:** Ảnh cửa hàng + Biểu đồ tròn phân bổ thiệt hại

---

## SLIDE 4: 7 GIẢI PHÁP CỤ THỂ (Phạm Năng Ân - 1 phút)

```
┌─────────────────────────────────────────────┐
│         VẤN ĐỀ → GIẢI PHÁP CỤ THỂ         │
├─────────────────────────────────────────────┤
│                                             │
│  1️⃣  Kho kém → Module Inventory + FEFO    │
│     ✓ FEFO tự động xếp thuốc hết hạn trước │
│     ✓ SMS cảnh báo khi HSD < 90 ngày       │
│     ✓ Kiểm kê tự động: 8h → 2h             │
│     → Giảm 27.9M → 0 VNĐ thiệt hại         │
│                                             │
│  2️⃣  Bán chậm → OCR + POS Tự động         │
│     ✓ AI OCR đọc đơn: 5 giây (95% chính xác)│
│     ✓ Auto kiểm tra DDI (tương tác thuốc)  │
│     ✓ BHYT tự động thanh toán              │
│     → Giảm thời gian: 8-12' → 2-3'         │
│                                             │
│  3️⃣  CRM yếu → Module CRM + Loyalty       │
│     ✓ Lưu lịch sử mua hàng                 │
│     ✓ Tích điểm loyalty point              │
│     ✓ SMS nhắc tái khám                    │
│     → Giữ chân 15-20% khách hàng           │
│                                             │
│  4️⃣  Dự báo kém → AI Forecasting          │
│     ✓ Prophet model học từ lịch sử         │
│     ✓ Auto đặt hàng khi tồn < ngưỡng       │
│     → Giảm thiếu hàng từ 40% → 5%          │
│                                             │
│  5️⃣  HR thủ công → Module HR Auto         │
│     ✓ Chấm công QR code                    │
│     ✓ Tính lương tự động                   │
│                                             │
│  6️⃣  Data rời → 1 Database PostgreSQL     │
│     ✓ Tích hợp 5 Excel → 1 CSDL            │
│                                             │
│  7️⃣  Hạ tầng yếu → AWS Cloud HA/DR        │
│     ✓ Backup tự động hàng ngày             │
│     ✓ HA 99.9% uptime                      │
└─────────────────────────────────────────────┘
```

**Sơ đồ:** Bảng mapping màu sắc Vấn đề → Giải pháp

---

## SLIDE 5: USE CASE & QUY TRÌNH (Nguyễn Bảo Tuấn - 2 phút)

```
┌─────────────────────────────────────────────┐
│    20 CHỨC NĂNG & QUY TRÌNH BÁN HÀNG       │
├─────────────────────────────────────────────┤
│                                             │
│  🎯 20 USE CASES                           │
│     🛒 Bán hàng (5): POS, đơn thuốc, DDI  │
│     📦 Kho (5): FEFO, cảnh báo HSD        │
│     👥 CRM (3): Lịch sử, loyalty          │
│     📊 BI (2): Dashboard, báo cáo         │
│     ⚙️  Admin (5): User, phân quyền       │
│                                             │
│  ⏱️  QUY TRÌNH BÁN - TRƯỚC & SAU          │
│                                             │
│  ❌ TRƯỚC: Thủ công → 8-12 phút           │
│     1. Đọc đơn thuốc thủ công (2-3')      │
│     2. Tìm thuốc trong kho                 │
│     3. Ghi số lô thủ công                  │
│     4. Tính tiền máy tính                  │
│     5. Ghi sổ Excel                        │
│                                             │
│  ✅ SAU: Tự động → 2-3 phút (70% nhanh)   │
│     1. Scan/Chụp đơn thuốc                 │
│     2. OCR đọc tự động (5 giây)            │
│     3. Auto check DDI                      │
│     4. FEFO pick lô tự động                │
│     5. Tính tiền + BHYT tự động            │
│                                             │
│  📐 Sơ đồ: Use Case + Activity Diagram    │
└─────────────────────────────────────────────┘
```

**Sơ đồ:** Use Case Diagram + Activity Diagram (2 in 1)

---

## SLIDE 6: KIẾN TRÚC HỆ THỐNG (Bùi Đức Tùng - 2.5 phút)

```
┌─────────────────────────────────────────────┐
│      KIẾN TRÚC 3-TIER & 8 MODULE           │
├─────────────────────────────────────────────┤
│                                             │
│  🏗️  KIẾN TRÚC 3 TẦNG                     │
│     • Presentation: Web + Mobile + POS     │
│     • Business: 8 Microservices            │
│     • Data: PostgreSQL + Redis + DWH       │
│                                             │
│  ⚙️  8 MODULE GIẢI 7 VẤN ĐỀ               │
│     1️⃣  Inventory Module                 │
│         → Giải Vấn đề 1 (Quản lý kho)     │
│         • FEFO algorithm                   │
│         • SMS alert HSD < 90 ngày          │
│                                             │
│     2️⃣  POS + OCR Module                  │
│         → Giải Vấn đề 2 (Tốc độ bán)     │
│         • TensorFlow CNN OCR               │
│         • Auto DDI checking                │
│                                             │
│     3️⃣  CRM Module                        │
│         → Giải Vấn đề 3 (Khách hàng)      │
│         • Customer history                 │
│         • Loyalty points                   │
│                                             │
│     4️⃣  AI Forecasting                    │
│         → Giải Vấn đề 4 (Dự báo)          │
│         • Prophet ML model                 │
│         • Auto reorder                     │
│                                             │
│     5️⃣  HR Module → Vấn đề 5              │
│     6️⃣  BI Dashboard → Vấn đề 6           │
│     7️⃣  BHYT Integration → Vấn đề 7       │
│     8️⃣  E-prescription → An toàn          │
│                                             │
│  💾 DATABASE: 7 bảng chính                │
│     Product → Batch → Inventory →          │
│     Sale → Customer → Staff                │
└─────────────────────────────────────────────┘
```

**Sơ đồ:** Architecture 3-tier + ERD + Sequence Diagram

---

## SLIDE 7: CÔNG NGHỆ & TRIỂN KHAI (Phan Văn Định - 2.5 phút)

```
┌─────────────────────────────────────────────┐
│    TECHNOLOGY STACK & DEPLOYMENT           │
├─────────────────────────────────────────────┤
│                                             │
│  💻 CÔNG NGHỆ                              │
│     • Frontend: React 18 + TypeScript      │
│     • Backend: Node.js + Python FastAPI    │
│     • DB: PostgreSQL 15 + Redis            │
│     • AI: TensorFlow (OCR 95% accuracy)    │
│     • Cloud: AWS (EC2, RDS, S3, Lambda)    │
│                                             │
│  🤖 AI/OCR ĐỌC ĐƠN THUỐC - GIẢI VẤN ĐỀ 2 │
│     • Input: Ảnh chụp/PDF đơn thuốc        │
│     • AI Processing:                       │
│       - Deep Learning CNN                  │
│       - Train với 10,000+ đơn mẫu          │
│       - NLP hiểu ngữ cảnh y tế             │
│     • Output: JSON danh sách thuốc         │
│     • Thời gian: < 5 giây                  │
│     • Độ chính xác: 95%                    │
│     → Giảm 80% thời gian đọc đơn           │
│                                             │
│  ☁️  DEPLOYMENT AWS - GIẢI VẤN ĐỀ 7       │
│     • Load Balancer + Auto Scaling         │
│     • Database: RDS Multi-AZ               │
│     • Backup: S3 tự động hàng ngày         │
│     • HA/DR: 99.9% uptime                  │
│     • Monitoring: CloudWatch               │
│                                             │
│  📅 ROADMAP 12 THÁNG                       │
│     Q1: Infrastructure + Auth + POS cơ bản │
│     Q2: OCR + DDI + FEFO                   │
│     Q3: BHYT + AI Forecasting + Mobile     │
│     Q4: UAT + Training + Go-live           │
└─────────────────────────────────────────────┘
```

**Sơ đồ:** Deployment Diagram AWS + Component Diagram

---

## SLIDE 8: QUẢN LÝ DỰ ÁN & KPI (Đào Duy Minh - 2 phút)

```
┌─────────────────────────────────────────────┐
│    AGILE, RỦI RO & KPI ĐÁNH GIÁ            │
├─────────────────────────────────────────────┤
│                                             │
│  🔄 PHƯƠNG PHÁP AGILE                      │
│     • 2 tuần/sprint × 24 sprints/năm       │
│     • Daily standup 15 phút                │
│     • Sprint review & Retrospective        │
│     • Linh hoạt thay đổi requirements      │
│                                             │
│  ⚠️  5 RỦI RO & GIẢI PHÁP                 │
│     1. OCR không đủ chính xác              │
│        → Manual entry backup               │
│        → Train với 10K+ mẫu đa dạng        │
│                                             │
│     2. Quy định Bộ Y tế thay đổi           │
│        → Thiết kế linh hoạt, dễ điều chỉnh │
│        → Tham vấn luật sư chuyên ngành     │
│                                             │
│     3. BHYT API thay đổi                   │
│        → Adapter pattern                   │
│        → Phương án dự phòng offline        │
│                                             │
│     4. Nhân viên kháng cự thay đổi         │
│        → Đào tạo kỹ lưỡng                  │
│        → Change management                 │
│                                             │
│     5. Vượt ngân sách                      │
│        → Review hàng tháng                 │
│        → Dự phòng 15%                      │
│                                             │
│  📚 ĐÀO TẠO                                │
│     • Dược sĩ: 40h (OCR, DDI, tư vấn)     │
│     • Thủ kho: 32h (FEFO, báo cáo)        │
│     • Thu ngân: 24h (POS, BHYT)            │
│     • Quản lý: 16h (Dashboard, KPI)        │
│                                             │
│  🎯 KPI ĐO LƯỜNG THÀNH CÔNG                │
│     ⏱️ Thời gian phục vụ: 10' → 3'         │
│     ✅ Độ chính xác kho: 85% → 99%         │
│     📈 Doanh thu/giao dịch: +15%           │
│     😊 NPS Score: > 8/10                   │
│     💰 Tiết kiệm: 33M VNĐ/6 tháng          │
└─────────────────────────────────────────────┘
```

---

## SLIDE 9: KẾT LUẬN (Cả nhóm - 1 phút)

```
┌─────────────────────────────────────────────┐
│      7 VẤN ĐỀ → 1 HỆ THỐNG → KẾT QUẢ      │
├─────────────────────────────────────────────┤
│                                             │
│  ✅ TỔNG KẾT GIẢI PHÁP                     │
│     • 8 module tích hợp                    │
│     • AI/OCR + FEFO tự động hóa            │
│     • AWS Cloud HA 99.9%                   │
│     • 12 tháng triển khai Agile            │
│                                             │
│  🎯 KẾT QUẢ GIẢI QUYẾT VẤN ĐỀ              │
│     1️⃣ Kho: 27.9M → 0 VNĐ thiệt hại      │
│     2️⃣ Tốc độ: 8-12' → 2-3' (70% nhanh)  │
│     3️⃣ CRM: Giữ 15-20% khách hàng        │
│     4️⃣ Dự báo: Thiếu 40% → 5%            │
│     5️⃣ HR: Tự động, 0 sai sót lương      │
│     6️⃣ Data: 5 Excel → 1 Database         │
│     7️⃣ Hạ tầng: Backup auto, 99.9% uptime│
│                                             │
│  👥 LỢI ÍCH CHO TẤT CẢ                     │
│     🏢 Công ty: Giảm 33M VNĐ/6T, +15% DT  │
│     👨‍⚕️ Nhân viên: -Stress, +Năng suất   │
│     😊 Khách hàng: Nhanh, An toàn, Tiện lợi│
│                                             │
│  🌟 TẦM NHÌN                               │
│     "Leading Pharmacy Tech in SEA by 2029" │
│                                             │
│  🎓 CẢM ƠN THẦY VÀ CÁC BẠN!                │
└─────────────────────────────────────────────┘
```

**Hình ảnh:** Logo trường + Long Châu

---

## 📝 HƯỚNG DẪN SỬ DỤNG (9 SLIDES)

### ✅ Phân công thời gian:

| Slide | Người thuyết trình | Thời gian | Nội dung chính                    |
| ----- | ------------------ | --------- | --------------------------------- |
| 1-2   | Cả nhóm            | 30s       | Giới thiệu, thành viên            |
| 3     | Phạm Năng Ân       | 2 phút    | **7 VẤN ĐỀ** chi tiết             |
| 4     | Phạm Năng Ân       | 1 phút    | **7 GIẢI PHÁP** cụ thể            |
| 5     | Nguyễn Bảo Tuấn    | 2 phút    | Use Case + Quy trình Before/After |
| 6     | Bùi Đức Tùng       | 2.5 phút  | Kiến trúc + 8 Module + Database   |
| 7     | Phan Văn Định      | 2.5 phút  | Công nghệ + OCR + AWS Deployment  |
| 8     | Đào Duy Minh       | 2 phút    | Agile + Rủi ro + Đào tạo + KPI    |
| 9     | Cả nhóm            | 1.5 phút  | Kết luận tổng hợp + Cảm ơn        |

**TỔNG:** ~14 phút thuyết trình + 1 phút Q&A = **15 phút**

### 🎯 ĐIỂM MẠNH CỦA CẤU TRÚC NÀY:

✅ **Tập trung vào VẤN ĐỀ - GIẢI PHÁP** (Slide 3 & 4)
✅ **Mapping rõ ràng:** Mỗi module giải quyết vấn đề nào
✅ **Không có phần Tài chính ROI** - Như yêu cầu
✅ **Chi tiết kỹ thuật:** OCR, FEFO, AI Forecasting
✅ **Có KPI đo lường** thay vì ROI tài chính

### 🎨 Màu sắc & Font:

- **Primary:** #0066CC (Xanh dương)
- **Secondary:** #00AA55 (Xanh lá Long Châu)
- **Accent:** #FF6600 (Cam - Highlight vấn đề)
- **Tiêu đề:** Arial Bold 32pt
- **Nội dung:** Arial Regular 18pt

### 📐 Sơ đồ cần chèn:

- **Slide 3:** Biểu đồ tròn phân bổ 7 vấn đề
- **Slide 4:** Bảng mapping Vấn đề → Giải pháp (2 cột, màu sắc)
- **Slide 5:** Use Case Diagram + Activity Diagram
- **Slide 6:** Architecture 3-tier + ERD + Sequence Diagram
- **Slide 7:** Deployment Diagram AWS + Component Diagram

### 🎯 Tips thuyết trình:

1. **Slide 3-4 là TRỌNG TÂM** - Phạm Năng Ân cần nói rõ, tự tin
2. **Kể câu chuyện thực tế:** "Bà cụ 70 tuổi mua thuốc, phải đợi 12 phút..."
3. **Nhấn mạnh con số:** 27.9M, 8-12 phút, 40% thiếu hàng
4. **Giải pháp cụ thể:** Không chỉ nói "Module Inventory" mà giải thích "FEFO + SMS alert"
5. **Pointer:** Chỉ rõ từng vấn đề → giải pháp tương ứng
6. **Handoff mượt:** "Tiếp theo, bạn Tuấn sẽ trình bày Use Case..."

---

**File này tối ưu cho thuyết trình 15 phút, tập trung VẤN ĐỀ - GIẢI PHÁP!** 🎯
