# 📊 SLIDE THUYẾT TRÌNH - HỆ THỐNG QUẢN LÝ NHÀ THUỐC LONG CHÂU

> **Format:** PowerPoint / Google Slides
> **Thời gian:** 15 phút
> **Số slide:** 11 slides (Phạm Năng Ân 2p, 5 người khác mỗi người 2p, kết luận 1.5p)

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
│     Phần: Tổng quan & Giới thiệu           │
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
│  5. Hoàng Văn Cường     - Thành viên       │
│     Phần: Phân tích tài chính              │
│                                             │
│  6. Đào Duy Minh        - Thành viên       │
│     Phần: Quản lý dự án                    │
└─────────────────────────────────────────────┘
```

---

## SLIDE 3: ĐỀ TÀI & 7 VẤN ĐỀ (Phạm Năng Ân - 2 phút)

```
┌─────────────────────────────────────────────┐
│    LONG CHÂU 175 TÂY SƠN - 7 VẤN ĐỀ       │
├─────────────────────────────────────────────┤
│                                             │
│  � CƠ SỞ NGHIÊN CỨU                       │
│     • 175 Tây Sơn, Hà Nội (gần BV Bạch Mai)│
│     • 120m², 4,200 SKU, 800-1,200 khách/ngày│
│     • Doanh thu: 650-750M VNĐ/tháng        │
│                                             │
│  ⚠️  7 VẤN ĐỀ CHÍNH                        │
│  1️⃣  Quản lý kho kém → 27.9M VNĐ          │
│  2️⃣  Bán hàng chậm → 8-12 phút            │
│  3️⃣  CRM yếu → Mất 15-20% khách           │
│  4️⃣  Dự báo kém → Thiếu 40% mùa đông      │
│  5️⃣  HR thủ công → Sai lương 1.8M         │
│  6️⃣  Dữ liệu rời → 5 file Excel           │
│  7️⃣  Hạ tầng yếu → Mất data 2 lần         │
│                                             │
│  💰 TỔNG THIỆT HẠI: 33M VNĐ/6 tháng       │
└─────────────────────────────────────────────┘
```

**Hình ảnh:** Ảnh cửa hàng + Biểu đồ tròn thiệt hại

---

## SLIDE 4: 7 VẤN ĐỀ → 7 GIẢI PHÁP (Phạm Năng Ân - 30 giây tiếp)

```
┌─────────────────────────────────────────────┐
│         VẤN ĐỀ → GIẢI PHÁP CỤ THỂ         │
├─────────────────────────────────────────────┤
│                                             │
│  1️⃣  Kho kém (27.9M) → Module Inventory   │
│     ✓ FEFO tự động xếp thuốc hết hạn trước │
│     ✓ Cảnh báo SMS khi HSD < 90 ngày       │
│                                             │
│  2️⃣  Bán chậm (8-12') → OCR + POS         │
│     ✓ Đọc đơn tự động 5 giây (AI CNN)     │
│     ✓ Auto kiểm tra DDI + BHYT             │
│                                             │
│  3️⃣  CRM yếu (mất 15-20% khách) → CRM     │
│     ✓ Lưu lịch sử mua + Loyalty point      │
│     ✓ SMS nhắc tái khám                    │
│                                             │
│  4️⃣  Dự báo kém (thiếu 40%) → AI Forecast │
│     ✓ Prophet model dự báo nhu cầu         │
│     ✓ Auto đặt hàng khi tồn < ngưỡng       │
│                                             │
│  5️⃣  HR thủ công → Module HR              │
│     ✓ Chấm công QR + Tính lương tự động   │
│                                             │
│  6️⃣  Data rời (5 Excel) → BI Dashboard    │
│     ✓ 1 database duy nhất PostgreSQL       │
│                                             │
│  7️⃣  Hạ tầng yếu → AWS Cloud              │
│     ✓ Backup tự động + HA 99.9%            │
└─────────────────────────────────────────────┘
```

---

## SLIDE 5: USE CASE & QUY TRÌNH (Nguyễn Bảo Tuấn - 2 phút)

```
┌─────────────────────────────────────────────┐
│    20 CHỨC NĂNG & QUY TRÌNH BÁN HÀNG       │
├─────────────────────────────────────────────┤
│                                             │
│  🎯 20 USE CASES                           │
│     � Bán hàng (5): POS, đơn thuốc, DDI  │
│     📦 Kho (5): FEFO, cảnh báo HSD        │
│     👥 CRM (3): Lịch sử, loyalty          │
│     📊 BI (2): Dashboard, báo cáo         │
│     ⚙️  Admin (5): User, phân quyền       │
│                                             │
│  ⏱️  QUY TRÌNH BÁN - TRƯỚC & SAU          │
│                                             │
│  ❌ Trước: Thủ công → 8-12 phút           │
│     Đọc đơn → Tìm thuốc → Ghi sổ          │
│                                             │
│  ✅ Sau: Tự động → 2-3 phút (70% nhanh)   │
│     OCR scan → Auto DDI → FEFO pick        │
│     → BHYT → Thanh toán                    │
│                                             │
│  📐 Sơ đồ: Use Case + Activity Diagram    │
└─────────────────────────────────────────────┘
```

**Sơ đồ:** Use Case + Activity Diagram (2 in 1)

---

## SLIDE 6: KIẾN TRÚC & DATABASE (Bùi Đức Tùng - 2 phút)

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
│     1️⃣  Inventory → Kho FEFO             │
│     2️⃣  POS + OCR → Tốc độ               │
│     3️⃣  CRM → Khách hàng                 │
│     4️⃣  AI Forecast → Dự báo             │
│     5️⃣  HR → Nhân sự                     │
│     6️⃣  BI → Tích hợp dữ liệu            │
│     7️⃣  BHYT → Bảo hiểm                  │
│     8️⃣  E-prescription → An toàn         │
│                                             │
│  � DATABASE: 7 bảng chính                │
│     Product → Batch → Inventory →          │
│     Sale → Customer → Staff                │
└─────────────────────────────────────────────┘
```

**Sơ đồ:** Architecture 3-tier + ERD

---

## SLIDE 7: CÔNG NGHỆ & TRIỂN KHAI (Phan Văn Định - 2 phút)

```
┌─────────────────────────────────────────────┐
│    TECHNOLOGY STACK & DEPLOYMENT           │
├─────────────────────────────────────────────┤
│                                             │
│  💻 CÔNG NGHỆ                              │
│     • Frontend: React 18 + TypeScript      │
│     • Backend: Node.js + Python            │
│     • DB: PostgreSQL 15 + Redis            │
│     • AI: TensorFlow (OCR 95% accuracy)    │
│                                             │
│  🤖 AI/OCR ĐỌC ĐƠN THUỐC                  │
│     • Input: Ảnh chụp/PDF đơn thuốc        │
│     • AI: CNN train với 10K+ mẫu           │
│     • Output: JSON danh sách thuốc         │
│     • Thời gian: < 5 giây                  │
│     • Độ chính xác: 95%                    │
│     → Giảm 80% thời gian đọc đơn           │
│                                             │
│  ☁️  DEPLOYMENT AWS                        │
│     • Load Balancer + Auto Scaling         │
│     • HA/DR: 99.9% uptime                  │
│     • 12 tháng triển khai (4 quarters)     │
└─────────────────────────────────────────────┘
```

**Sơ đồ:** Deployment Diagram AWS

---

## SLIDE 8: TÀI CHÍNH & ROI (Hoàng Văn Cường - 2 phút)

```
┌─────────────────────────────────────────────┐
│         PHÂN TÍCH TÀI CHÍNH - ROI          │
├─────────────────────────────────────────────┤
│                                             │
│  💰 CHI PHÍ ĐẦU TƯ: 1,650M VNĐ            │
│     • Phần mềm: 800M (48%)                 │
│     • Phần cứng: 300M (18%)                │
│     • Triển khai: 400M (24%)               │
│     • Đào tạo: 100M + Dự phòng: 50M        │
│                                             │
│  � CHI PHÍ VẬN HÀNH: 1,644M/năm          │
│  � LỢI ÍCH: 1,776M VNĐ/năm               │
│     • Tiết kiệm nhân sự: 720M              │
│     • Giảm thất thoát: 480M                │
│     • Tăng doanh thu: 420M                 │
│     • Khác: 156M                           │
│                                             │
│  ✅ KẾT QUẢ                                │
│     • NPV (8%): +1,234M VNĐ                │
│     • IRR: 24.5%                           │
│     • Payback: 3.2 năm                     │
│     • ROI 5 năm: 72.8%                     │
│                                             │
│  📊 So sánh: Rẻ hơn SAP 60%                │
└─────────────────────────────────────────────┘
```

**Biểu đồ:** Cash flow 5 năm

---

## SLIDE 9: QUẢN LÝ DỰ ÁN (Đào Duy Minh - 2 phút)

```
┌─────────────────────────────────────────────┐
│    AGILE, RỦI RO & ĐÀO TẠO                 │
├─────────────────────────────────────────────┤
│                                             │
│  🔄 PHƯƠNG PHÁP AGILE                      │
│     • 2 tuần/sprint × 24 sprints/năm       │
│     • Daily standup + Sprint review        │
│     • Linh hoạt thay đổi requirements      │
│                                             │
│  ⚠️  5 RỦI RO CHÍNH & GIẢI PHÁP           │
│     1. OCR không chính xác → Manual backup │
│     2. Quy định thay đổi → Thiết kế linh hoạt│
│     3. BHYT API thay đổi → Adapter pattern │
│     4. Nhân viên kháng cự → Đào tạo kỹ    │
│     5. Vượt ngân sách → Dự phòng 15%       │
│                                             │
│  � ĐÀO TẠO                                │
│     • Dược sĩ: 40h (OCR, DDI, tư vấn)     │
│     • Thủ kho: 32h (FEFO, báo cáo)        │
│     • Thu ngân: 24h (POS, BHYT)            │
│     • Quản lý: 16h (Dashboard, KPI)        │
│                                             │
│  🎯 KPI THÀNH CÔNG                         │
│     Thời gian: 10'→3' | Accuracy: 85→99%   │
│     Doanh thu: +15% | NPS: >8/10           │
└─────────────────────────────────────────────┘
```

---

## SLIDE 10: KẾT LUẬN & LỢI ÍCH (Cả nhóm - 1 phút)

```
┌─────────────────────────────────────────────┐
│      7 VẤN ĐỀ → 1 HỆ THỐNG → KẾT QUẢ      │
├─────────────────────────────────────────────┤
│                                             │
│  ✅ GIẢI PHÁP TOÀN DIỆN                    │
│     • 8 module tích hợp                    │
│     • AI/OCR tự động hóa                   │
│     • Cloud deployment                     │
│     • 12 tháng triển khai                  │
│                                             │
│  🎯 KẾT QUẢ MONG ĐỢI                       │
│     • Giảm 70% thời gian phục vụ           │
│     • Tiết kiệm 27.9M VNĐ/6 tháng          │
│     • Tăng 15% doanh thu                   │
│     • ROI 72.8% trong 5 năm                │
│                                             │
│  👥 LỢI ÍCH CHO TẤT CẢ                     │
│     � Công ty: +Lợi nhuận, +Hiệu quả     │
│     👨‍⚕️ Nhân viên: -Stress, +Năng suất   │
│     😊 Khách hàng: Nhanh, An toàn, Tiện lợi│
│                                             │
│  � TẦM NHÌN: Leading Pharmacy Tech SEA    │
└─────────────────────────────────────────────┘
```

---

## SLIDE 11: Q&A & CẢM ƠN

```
┌─────────────────────────────────────────────┐
│              HỎI & ĐÁP                     │
├─────────────────────────────────────────────┤
│                                             │
│                    ❓                       │
│                                             │
│         NHÓM SẴN SÀNG TRẢ LỜI              │
│         CÁC CÂU HỎI CỦA THẦY               │
│              VÀ CÁC BẠN                    │
│                                             │
│  📧 Contact:                               │
│     Email: nhom3.64httt4@tlu.edu.vn        │
│                                             │
│  🎓 CẢM ƠN THẦY VÀ CÁC BẠN! 🎓            │
│                                             │
│     Nhóm 3 - Lớp 64HTTT4                   │
│     Trường Đại học Thủy lợi                │
│                                             │
│   "Technology for Better Healthcare"       │
└─────────────────────────────────────────────┘
```

**Hình ảnh:** Logo trường + Long Châu

---

## 📝 HƯỚNG DẪN SỬ DỤNG (11 SLIDES)

### ✅ Phân công thời gian:

| Slide | Người thuyết trình | Thời gian | Nội dung chính             |
| ----- | ------------------ | --------- | -------------------------- |
| 1-2   | Cả nhóm            | 30s       | Giới thiệu, thành viên     |
| 3     | Phạm Năng Ân       | 1.5 phút  | 7 vấn đề tại 175 Tây Sơn   |
| 4     | Phạm Năng Ân       | 30s       | **7 Vấn đề → 7 Giải pháp** |
| 5     | Nguyễn Bảo Tuấn    | 2 phút    | Use Case + Quy trình       |
| 6     | Bùi Đức Tùng       | 2 phút    | Kiến trúc + Database       |
| 7     | Phan Văn Định      | 2 phút    | Công nghệ + Deployment     |
| 8     | Hoàng Văn Cường    | 2 phút    | Tài chính + ROI            |
| 9     | Đào Duy Minh       | 2 phút    | Agile + Rủi ro + KPI       |
| 10    | Cả nhóm            | 1 phút    | Kết luận tổng hợp          |
| 11    | Cả nhóm            | 30s + Q&A | Cảm ơn + Trả lời           |

**TỔNG:** ~13.5 phút thuyết trình + 1.5 phút Q&A = **15 phút**

### 🎨 Màu sắc & Font:

- **Primary:** #0066CC (Xanh dương)
- **Secondary:** #00AA55 (Xanh lá Long Châu)
- **Tiêu đề:** Arial Bold 32pt
- **Nội dung:** Arial Regular 18pt

### 📐 Sơ đồ cần chèn:

- **Slide 3:** Biểu đồ tròn phân bổ thiệt hại
- **Slide 4:** Bảng mapping Vấn đề → Giải pháp (có thể dùng icon/màu sắc)
- **Slide 5:** Use Case Diagram + Activity Diagram
- **Slide 6:** Architecture 3-tier + ERD
- **Slide 7:** Deployment Diagram AWS
- **Slide 8:** Line chart cash flow 5 năm

### 🎯 Tips thuyết trình:

1. **Mỗi người 2 phút** - Tập luyện với đồng hồ
2. **Nói tự nhiên** - Không đọc slide
3. **Kể câu chuyện** - Ví dụ về bà cụ mua thuốc
4. **Pointer** - Chỉ vào điểm quan trọng
5. **Handoff mượt** - "Tiếp theo, bạn Tuấn sẽ trình bày..."
6. **Backup Q&A** - Chuẩn bị 10 câu hỏi có thể có

---

**File này tối ưu cho thuyết trình 15 phút!** 🎉
