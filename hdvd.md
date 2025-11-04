# ĐẠO ĐỨC AI TRONG HỆ THỐNG QUẢN LÝ NHÀ THUỐC LONG CHÂU 175 TÂY SƠN

## 1. TẦM QUAN TRỌNG CỦA ĐẠO ĐỨC AI TRONG HỆ THỐNG DƯỢC

Hệ thống quản lý nhà thuốc Long Châu 175 Tây Sơn tích hợp 4 chức năng AI chính:

1. **OCR đọc đơn thuốc** - Tự động nhận dạng đơn từ bác sĩ
2. **DDI Engine** - Kiểm tra tương tác thuốc-thuốc
3. **AI Forecasting** - Dự báo nhu cầu thuốc theo mùa
4. **CRM Chatbot** - Tư vấn sức khỏe và thuốc OTC

**Tại sao đạo đức AI nghiêm trọng?**

- Sai sót AI có thể gây **tử vong** (ví dụ: không phát hiện tương tác Warfarin + Aspirin → xuất huyết não)
- 27.9 triệu VNĐ thiệt hại/6 tháng do quản lý kém → AI cần chính xác để tránh tăng rủi ro
- 70% bệnh nhân Việt Nam tự mua thuốc → Dễ bị ảnh hưởng bởi AI tư vấn sai

---

## 2. 5 NGUYÊN TẮC ĐẠO ĐỨC CỐT LÕI

## 2. 5 NGUYÊN TẮC ĐẠO ĐỨC CỐT LÕI

### 2.1. KHÔNG GÂY HẠI (Non-Maleficence)

**Áp dụng cụ thể trong hệ thống:**

| Tính năng AI          | Rủi ro                                           | Biện pháp phòng ngừa                                                                                   |
| --------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **OCR đọc đơn thuốc** | Đọc sai "10mg" → "100mg" → Quá liều 10 lần       | • Confidence ≥ 95% mới hiển thị<br>• Alert đỏ nếu liều > khuyến cáo<br>• **Dược sĩ bắt buộc xác nhận** |
| **DDI Engine**        | Không cảnh báo Warfarin + Aspirin → Xuất huyết   | • Cập nhật DB hàng tháng từ FDA<br>• Hard-code chống chỉ định tuyệt đối<br>• Block bán nếu DDI mức 5/5 |
| **AI Forecasting**    | Dự báo thấp → Thiếu Insulin → Tử vong            | • Safety stock +50% cho thuốc cứu mạng<br>• Alert khi tồn < 7 ngày                                     |
| **CRM Chatbot**       | Khuyên Aspirin cho trẻ <12 tuổi → Hội chứng Reye | • Không tư vấn thuốc kê đơn<br>• Bắt buộc hỏi tuổi/tiền sử                                             |

**Cam kết:** Mọi khuyến nghị AI phải được dược sĩ xác nhận trước khi cung cấp cho bệnh nhân.

---

### 2.2. LÀM ĐIỀU TỐT (Beneficence)

**Vấn đề:** AI có thể ưu tiên lợi nhuận thay vì lợi ích bệnh nhân

**Giải pháp trong hệ thống:**

- **Module Inventory:** Gợi ý thuốc FEFO (hết hạn trước xuất trước) → Giảm 27.9M thiệt hại
- **POS System:** Hiển thị thuốc generic rẻ hơn làm lựa chọn mặc định
  ```
  Ví dụ: Augmentin 625mg (120K) → Generic Amoxicillin (35K) - Tiết kiệm 85K cho khách
  ```
- **AI Forecast:** Dự báo chính xác để tránh thiếu hàng (giảm 40% → 5% shortage)

**KPI đo lường đạo đức:**

- Tỷ lệ gợi ý generic: >60%
- NPS Score: >8/10
- Tỷ lệ khách quay lại: >75%

---

### 2.3. QUYỀN TỰ QUYẾT (Autonomy)

**1. Consent sử dụng dữ liệu:**

```
Khi đăng ký CRM, hệ thống hiển thị:
☑ Tôi đồng ý Long Châu lưu lịch sử mua thuốc để tư vấn tốt hơn
☑ Tôi có quyền yêu cầu xóa dữ liệu bất kỳ lúc nào
```

**2. Quyền từ chối AI:**

- Nút "Tôi muốn nói với dược sĩ người" luôn hiển thị trên chatbot
- Không bắt buộc dùng AI OCR nếu dược sĩ muốn đọc tay

**3. Minh bạch:**

```
🤖 Chatbot:
"Đây là tư vấn sơ bộ từ AI, KHÔNG THAY THẾ bác sĩ.
Triệu chứng nghiêm trọng → GỌI 115"
```

---

### 2.4. CÔNG BẰNG (Justice)

**Rủi ro bias trong hệ thống:**

| Loại Bias | Nguy cơ                               | Giải pháp                              |
| --------- | ------------------------------------- | -------------------------------------- |
| Kinh tế   | AI ưu tiên gợi ý thuốc đắt cho VIP    | Thuật toán không xem hạng khách hàng   |
| Tuổi tác  | OCR train chủ yếu trên đơn người trẻ  | Validate trên 10K+ đơn đa dạng độ tuổi |
| Địa lý    | Dự báo chính xác ở HN, sai ở vùng cao | Thu thập data từ nhiều chi nhánh       |

**Audit 6 tháng/lần:**

- So sánh khuyến nghị AI cho nhóm khách hàng khác nhau
- Công bố báo cáo tỷ lệ gợi ý thuốc đắt/rẻ

---

### 2.5. GIẢI THÍCH ĐƯỢC (Explainability)

**Mọi quyết định AI phải có lý do:**

❌ **Không chấp nhận:**

```
"Hệ thống không khuyên dùng thuốc X"
```

✅ **Chấp nhận:**

```
"Không khuyên dùng thuốc X vì:
 • Bạn đang dùng thuốc Y
 • X + Y gây rối loạn nhịp tim (DDI-2341)
 • Nghiên cứu: FDA 2023, Lancet 2022"
```

**Yêu cầu kỹ thuật:**

```python
def recommend_drug(patient, symptoms):
    result = ai_model.predict(patient, symptoms)
    return {
        "drug": result.name,
        "reason": result.explanation,  # BẮT BUỘC
        "evidence": result.research_refs,
        "confidence": result.score
    }
```

---

## 3. RỦI RO VÀ BIỆN PHÁP CỤ THỂ

### 3.1. Ma trận Rủi ro Ưu tiên

| Rủi ro                      | Xác suất   | Tác động   | Mức độ          | Biện pháp                        |
| --------------------------- | ---------- | ---------- | --------------- | -------------------------------- |
| **OCR đọc sai liều**        | Cao        | Rất cao    | 🔴 Nghiêm trọng | Human-in-the-loop bắt buộc       |
| **DDI không phát hiện**     | Trung bình | Rất cao    | 🔴 Nghiêm trọng | Update DB hàng tháng + Hard-code |
| **Dự báo sai thiếu thuốc**  | Trung bình | Cao        | 🟡 Cao          | Safety stock +50%                |
| **Rò rỉ dữ liệu bệnh nhân** | Thấp       | Rất cao    | 🟡 Cao          | AES-256 + Access control         |
| **Chatbot tư vấn sai OTC**  | Cao        | Trung bình | 🟡 Cao          | Disclaimer + Không tư vấn Rx     |

### 3.2. Quy trình Xử lý Sự cố AI

**Khi phát hiện AI sai:**

```
0-2 giờ:  ⚠️ Tắt tính năng + Thông báo nhân viên + Liên hệ khách hàng
2-24 giờ: 🔍 Điều tra nguyên nhân + Đánh giá mức độ + Báo cáo Bộ Y tế (nếu cần)
1-7 ngày: 🔧 Fix bug + Test kỹ + Peer review
7-30 ngày: 📚 Cập nhật quy trình + Đào tạo lại + Công bố báo cáo
```

---

## 4. QUẢN TRỊ VÀ TUÂN THỦ

### 4.1. Hội đồng Đạo đức AI (5 thành viên)

- 1 Dược sĩ lâm sàng
- 1 Bác sĩ tư vấn
- 1 Chuyên gia AI/ML
- 1 Chuyên gia luật y tế
- 1 Đại diện khách hàng

**Nhiệm vụ:** Duyệt tính năng AI mới, điều tra sự cố, cập nhật quy tắc hàng quý

### 4.2. Tuân thủ Quy định

| Quy định                          | Yêu cầu                     | Áp dụng trong hệ thống        |
| --------------------------------- | --------------------------- | ----------------------------- |
| **Thông tư 01/2020/TT-BYT (GPP)** | Dược sĩ trực tiếp tư vấn Rx | AI chỉ hỗ trợ, không thay thế |
| **Nghị định 13/2023 (GDPR VN)**   | Quyền xóa dữ liệu           | CRM có nút "Xóa tài khoản"    |
| **Luật ATTT 2018**                | Báo cáo vi phạm 72h         | Incident response plan        |

### 4.3. Đào tạo Nhân viên

**Module bắt buộc (8 giờ):**

- Nguyên tắc đạo đức AI (2h)
- Cách kiểm tra khuyến nghị AI (3h)
- Xử lý sự cố AI (3h)

**Đánh giá:** 100% dược sĩ phải pass quiz trước khi dùng hệ thống

---

## 5. KẾT LUẬN

### Cam kết 5 KHÔNG - 5 CÓ

**5 KHÔNG:**

1. ❌ KHÔNG để AI tự quyết định thuốc kê đơn
2. ❌ KHÔNG ưu tiên lợi nhuận thay vì an toàn
3. ❌ KHÔNG dùng dữ liệu bệnh nhân không consent
4. ❌ KHÔNG che giấu khi AI đưa ra khuyến nghị
5. ❌ KHÔNG triển khai AI chưa test kỹ

**5 CÓ:**

1. ✅ CÓ dược sĩ kiểm tra mọi khuyến nghị quan trọng
2. ✅ CÓ giải thích rõ ràng cho mọi quyết định AI
3. ✅ CÓ quy trình xử lý sự cố 24/7
4. ✅ CÓ audit độc lập 6 tháng/lần
5. ✅ CÓ đào tạo 100% nhân viên

### Roadmap

| Năm      | Mục tiêu                                                                |
| -------- | ----------------------------------------------------------------------- |
| **2025** | Thành lập Hội đồng Đạo đức + Đào tạo 100% nhân viên + Human-in-the-loop |
| **2026** | Audit độc lập + Báo cáo minh bạch hàng năm                              |
| **2027** | ISO 42001 (AI Management) + Chia sẻ best practices ngành                |

---

## PHỤ LỤC: CHECKLIST TRIỂN KHAI AI

**Trước khi bật tính năng AI mới:**

- [ ] Đã test trên ≥1000 ca thực tế?
- [ ] Có hard-code safety rules?
- [ ] Dược sĩ có thể override AI?
- [ ] AI giải thích được quyết định?
- [ ] Dữ liệu train đa dạng (tuổi/vùng/giới)?
- [ ] Đã kiểm tra bias?
- [ ] Có disclaimer cho bệnh nhân?
- [ ] Có xin consent?
- [ [ ] Dữ liệu được mã hóa AES-256?
- [ ] Có incident response plan?
- [ ] Nhân viên đã được đào tạo?
- [ ] Hội đồng Đạo đức đã duyệt?

**NẾU CÓ 1 Ô CHƯA TICK → TẠM DỪNG TRIỂN KHAI**

---

## TÀI LIỆU THAM KHẢO

1. WHO (2021), "Ethics and governance of AI for health"
2. Bộ Y tế (2020), "Thông tư 01/2020/TT-BYT về GPP"
3. Chính phủ VN (2023), "Nghị định 13/2023/NĐ-CP về Bảo vệ dữ liệu cá nhân"
4. EU (2024), "Artificial Intelligence Act"
5. FDA (2023), "AI/ML in Medical Devices Guidelines"

---

_Tài liệu này là phần bắt buộc của Báo cáo "Xây dựng hệ thống quản lý Nhà thuốc Long Châu 175 Tây Sơn", thể hiện trách nhiệm đạo đức khi phát triển AI y tế._
