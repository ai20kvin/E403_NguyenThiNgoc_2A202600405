# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Tôi nhận thấy khi temperature = 0.0, câu trả lời rất nhất quán và ít mang tính sáng tạo. Khi tăng temperature lên 0.5 và 1.0, câu nói mượt mà, nhiều thông tin và đa dạng hơn. Tuy nhiên ở mức 1.5, văn bản sinh ra thường gặp lỗi ngữ pháp, dùng từ lộn xộn hoặc thông tin không còn chuẩn xác.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Mức lý tưởng là 0.0 đến 0.2. Lý do là chatbot CSKH cần cung cấp thông tin chính xác, ổn định và đáng tin cậy. Việc giữ temperature thấp giúp mô hình bám sát tài liệu hướng dẫn và hạn chế tối đa việc "ảo giác" (hallucinate) thông tin sai lệch dẫn đến ảnh hưởng trải nghiệm khách hàng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Dựa theo biểu giá (Output), GPT-4o có giá 0.010 USD / 1K token, trong khi GPT-4o-mini là 0.0006 USD / 1K token. Như vậy, GPT-4o đắt hơn khoảng 16.67 lần (0.010 / 0.0006) so với GPT-4o-mini với cùng một khối lượng token xử lý.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> - **GPT-4o xứng đáng:** Khi thực hiện các tác vụ phức tạp yêu cầu logic toán học, lập trình nâng cao, hoặc các nhận thức hình ảnh chuyên sâu, nơi chất lượng của từng câu trả lời quan trọng hơn chi phí.
> - **GPT-4o-mini tốt hơn:** Khi cần xử lý hàng loạt văn bản đơn giản (phân loại, tóm tắt) hoặc trong các tác vụ chatbot trò chuyện cơ bản hàng ngày, giúp tiết kiệm tối đa chi phí mà vẫn đảm bảo hiệu suất.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming cực kỳ quan trọng cho các ứng dụng tương tác thời gian thực như chatbot hay trợ lý ảo, giúp giảm thời gian phản hồi ban đầu (Time To First Byte), tạo cảm giác AI đang "gõ" trực tiếp. Điều này giữ chân người dùng khỏi sự sốt ruột. Ngược lại, non-streaming lại lý tưởng cho các quá trình chạy ngầm (background jobs) như trích xuất dữ liệu hàng loạt, dịch tài liệu, sinh báo cáo tự động hoặc gọi chain-of-agents, nơi mà hệ thống chỉ quan tâm kết quả trọn vẹn cuối cùng để chuyển qua bước tiếp theo.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
