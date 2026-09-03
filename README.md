# Track 1 — Day 25: AI Pricing · GTM · Evidence
## Monetization Model & Go-To-Market One-Pager

**Học viên:** Trần Kiên (Mã SV: `2A202601598`)  
**Sản phẩm:** VLearn AI Tutor Panel (Trợ lý AI hướng dẫn gỡ lỗi bài tập lập trình nhúng trực tiếp trong nền tảng VLearn)  
**Tài liệu bàn giao:**
1. `Day25-TranKien.xlsx`: File Excel 8 tabs tính toán chi tiết Cost/Job, Sanity Pricing, Value Metric Scorecard, Channel Fit, 90-Day Plan, Benchmarks và Checkpoints log.
2. `Day25-TranKien.docx`: Monetization One-Pager chuẩn hóa 1 trang, đồng bộ 100% dữ liệu với mô hình tài chính.
3. `README.md`: Báo cáo tổng quan, phân tích định lượng và biên bản tự kiểm toán (Checkpoint Audit).

---

## 1. Executive Summary & Các Chỉ Số Tài Chính Cốt Lõi

| Chỉ số | Giá trị | Đơn vị quy đổi | Nguồn ô tính trong Excel | Ghi chú & Đánh giá |
| :--- | :--- | :--- | :--- | :--- |
| **Đơn vị tính tiền (Value Metric)** | **HYBRID** | Gói nền 149.000đ/tháng (gồm 60 jobs) + Overage theo usage | `3_Value_Metric!B30` | Attribution = 6/10, Autonomy = 7/10. Bảo vệ chống heavy-user loss. |
| **Cost / Job (Pure COGS)** | **$0,0273** | **709 ₫ / job** | `1_Cost_Job!B66`, `2_Pricing!B5` | Chia cho 920 jobs hoàn thành (containment 92%). Có Prompt Caching tiết kiệm 46,1%. |
| **Giá sàn (3× Cost/Job)** | **$0,0818** | **2.127 ₫ / job** | `2_Pricing!B7` | Ngưỡng bù đắp chi phí vận hành, biến động token và sai số. |
| **Giá bán đề xuất** | **$0,0955** | **2.483 ₫ / job** (149.000đ / 60 jobs) | `2_Pricing!B19` | Đạt **3,50× Cost/Job** (≥ 3×). Neo 14,9% giá trị gia sư tiết kiệm (vùng 10–25%). |
| **Gross Margin (GM)** | **71,4%** | **71,4%** (base case off-peak) | `2_Pricing!B21` | Vượt chuẩn an toàn ngành (mục tiêu ≥ 60%, benchmark AI-native ~53%). |
| **Breakeven Containment** | **65,7%** | Tối thiểu cần đạt để GM ≥ 60% | `2_Pricing!B33` | An toàn so với Synthetic Eval hiện tại (**92,0%**). |
| **ARPU / tháng** | **$5,73** | **149.000 ₫ / tháng** | `4_Channel_Fit!B5` | Tỷ giá quy ước 26.000 ₫/USD. |
| **Ngân sách CAC tối đa** | **$49,13** | **1,28 triệu ₫ / khách** | `4_Channel_Fit!B9` | Công thức: ARPU × GM × 12 tháng payback. |
| **Inside Sales Deals / AE / Ngày** | **29,08** | deals / ngày làm việc | `4_Channel_Fit!B16` | **Bất khả thi về mặt số học** (chuẩn ≤ 1 deal/ngày) → Loại bỏ Sales-Led. |
| **Kênh GTM 90 ngày đầu** | **PLG** | In-product conversion trên VLearn | `4_Channel_Fit!B38` | Điểm scorecard: PLG = 29/30, Partner-Led = 17, Sales-Led = 8. |

---

## 2. Chi Tiết Kiến Trúc 4 Khối (Four Blocks)

### Khối 1: Ngân Sách Khách Hàng & Định Nghĩa Job
* **Ngân sách nhắm đến:** Ngân sách học tập & phát triển kỹ năng cá nhân (Prosumer / Junior Developer).
* **Định vị sản phẩm:** *"Panel AI Tutor nhúng trong VLearn gợi ý bước sửa lỗi code/lab cho học viên trong 5 phút đầu sau khi test fail, giảm thời gian tắc bài mà không cần gia sư trực tiếp."* (Đóng gói thay thế công việc/gia sư).
* **Định nghĩa 1 Job hoàn thành:** *1 phiên giải đáp hoàn thành khi học viên nhận hướng dẫn/gợi ý sửa lỗi và bấm "Đã hiểu" hoặc không gửi yêu cầu hỏi lại trong 10 phút.* (Đạt tiêu chuẩn 3 câu hỏi: Giá trị với khách hàng, đếm tự động qua log event, định nghĩa chặt chẽ).
* **Biến thể HITL:** Chọn **Biến thể A** (Khách tự escalate / tự debug nếu AI không giải quyết được; không tính chi phí nhân sự xử lý thay vào COGS của sản phẩm phần mềm).

### Khối 2: Value Metric & Sanity Pricing
* **Chấm điểm Ma trận:**
  * **Attribution = 6/10:** Đã có log chi tiết và synthetic eval 25 ca (92% pass), nhưng chưa có production traffic và khách chưa ký SLA kết quả học tập.
  * **Autonomy = 7/10:** AI tự chạy gợi ý ngoài giờ hành chính, QA nội bộ lấy mẫu 5%.
* **Lựa chọn:** **HYBRID** (Subscription 149.000đ/tháng cho 60 jobs hoàn thành + overage usage).
  * *Lý do thị trường:* Học viên Việt Nam cần chi phí hàng tháng cố định dự đoán được, đồng thời cơ chế quota/overage bảo vệ công ty khỏi rủi ro heavy-user lạm dụng token.
* **Benchmarks thực tế:**
  1. *GitHub Copilot Pro:* Hybrid ($10/tháng gồm 1.500 AI Credits; overage $0,01/AI Credit) — [GitHub Plans](https://docs.github.com/en/copilot/get-started/plans).
  2. *ChatGPT Plus:* Subscription ($20/tháng kèm usage limits) — [OpenAI Help](https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus).

### Khối 3: Cấu Trúc Chi Phí 5 Thành Phần (Cost/Job Model)
Giả định quy mô: 1.000 jobs thử/tháng, Containment rate = 92% → **920 jobs hoàn thành**.

| Thành phần chi phí | Cách tính & Giả định kỹ thuật | Chi phí / tháng | Chi phí / Job completed |
| :--- | :--- | :--- | :--- |
| **1. LLM API** | DeepSeek V4 Flash (off-peak $0,22/$0,007/$0,66 per 1M). 3 turns/session (3.500 in, 400 out), Prompt Caching 2.500 tokens input lặp lại. | $6,19 | $0,00673 |
| **2. Speech API** | Không có tính năng thoại ($0). | $0,00 | $0,00000 |
| **3. Infra** | Vector DB, embedding, session storage, logging ($0,0034/job thử). | $3,40 | $0,00370 |
| **4. Retry** | Tỷ lệ retry 8% do timeout/parse error ($6,19 × 8%). | $0,50 | $0,00054 |
| **5. HITL** | QA nội bộ lấy mẫu 5% ca, 2 phút/ca @ $9/h fully-loaded. | $15,00 | $0,01630 |
| **Tổng Pure COGS** | **Cộng 5 thành phần (chia cho 920 jobs hoàn thành)** | **$25,09** | **$0,02727 (≈ 709 ₫)** |

* **Hiệu quả Prompt Caching:** Giảm từ $0,00378 xuống $0,00204/job thử (**tiết kiệm 46,1% chi phí LLM**).
* **Độ nhạy (Sensitivity):** Mô hình chỉ gãy (Gross Margin < 50%) khi Containment rớt xuống dưới **52,5%** (ở giờ off-peak) hoặc dưới **66,5%** (ở giờ peak).

### Khối 4: Go-To-Market (GTM) & Kế Hoạch 90 Ngày
* **Pain Moment (Đủ 3 phần):** **20:00–23:00** (Mấy giờ) + **trong 5 phút đầu sau khi test code báo lỗi khi đang làm lab** (Đang làm gì) + **trang Lab & Code Editor VLearn** (Dùng app nào).
* **Điểm nhúng:** Panel AI Tutor tích hợp trực tiếp ngay trong giao diện làm bài lab của VLearn (Zero Friction).
* **Affordability Test:**
  * Ngân sách CAC = $49,13 (≈ 1,28 triệu ₫).
  * Chi phí cơ hội Sales Rep (ICONIQ 2026: $6.300/opp) → CAC thực tế có sales lên tới $25.200 → Gấp 512 lần ngân sách CAC → Bắt buộc chọn **PLG**.
* **Kế hoạch 90 ngày (3 giai đoạn):**
  * **Tháng 1 (Học):** 10 beta learners, log ≥100 sessions, 5 phỏng vấn chuyên sâu, sửa schema & trích dẫn code (Owner: Trần Kiên - PM, Deadline: 30/09/2026).
  * **Tháng 2–3 (Đòn bẩy):** 50 paying learners, chuẩn hóa onboarding, áp dụng allowance 60 jobs + paywall/overage, đạt Paid Conversion ≥5%, GM ≥60% (Owner: Trần Kiên + Tech Lead, Deadline: 30/11/2026).
  * **Tháng 4+ (Mở rộng):** 150 paying learners, mở rộng bài lab Python/Data, giữ CAC ≤350.000₫, GM ≥60% (Owner: PM Growth + Tech Lead, từ 01/12/2026).

---

## 3. Evidence Pack & Prompt Review Log (§4.7)

### Bảng Tiến Độ Evidence Pack
1. **Eval Results (Day 21–22):** Đã có bộ test 25 ca synthetic (23 pass, 1 fail, 1 uncertain → 92% pass; Schema 96%; Quote verbatim 29,2%). Trạng thái: **HOLD** (chưa đủ dữ liệu production để bán Outcome thuần). Hoàn thành 21/08/2026.
2. **Risk Checklist (Day 24):** Đã hoàn tất 3 rào cản phòng mua hàng: (1) Kiểm soát ảo giác & escalation, (2) Cam kết không dùng dữ liệu học viên train model, (3) Chính sách export/xóa dữ liệu minh bạch. Hoàn thành 26/08/2026.
3. **Pilot Report:** Kế hoạch thử nghiệm 4 tuần với 10 học viên thực tế, đo lường success rate thật và willingness-to-pay. Deadline: **30/09/2026** (Phụ trách: Trần Kiên).

### Prompt Review Log (§4.7)
* **Prompt 4.7.1 (Cost/Job Stress Test):**
  * *Phát hiện:* Giá DeepSeek có phân tách peak / off-peak.
  * *Quyết định:* **ACCEPT** — Cập nhật biểu giá off-peak cho khung giờ 20:00–23:00 và đưa kịch bản peak vào phân tích độ nhạy.
  * *Phát hiện mẫu số:* Nghi ngờ chia cho job thử.
  * *Quyết định:* **REJECT** — Chứng minh rõ công thức chia cho 920 jobs hoàn thành.
* **Prompt 4.7.5 (One-Pager Defensibility Check):**
  * *Phát hiện:* Tỷ lệ Eval 92% mới là synthetic 25 ca, chưa thể dùng làm production proof.
  * *Quyết định:* **ACCEPT** — Giữ nguyên nhãn verdict HOLD, không phóng đại số liệu khi định giá.
  * *Phát hiện thuật ngữ:* GitHub Copilot chuyển đổi mô hình định giá.
  * *Quyết định:* **ACCEPT** — Cập nhật chính xác thuật ngữ *AI Credits* và overage pricing theo cập nhật 2026.

---


