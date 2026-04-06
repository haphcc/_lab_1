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
> Qua bốn phản hồi, khi temperature thấp (0.0–0.5), câu trả lời ổn định hơn và thường bám cùng một hướng nội dung, chỉ khác nhẹ cách diễn đạt. Khi temperature tăng (1.0–1.5), nội dung đa dạng và sáng tạo hơn, dễ chuyển sang các “sự thật thú vị” khác nhau thay vì lặp lại một ý. Nói ngắn gọn, temperature càng cao thì độ ngẫu nhiên và biến thiên của phản hồi càng lớn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Mình sẽ đặt temperature khoảng 0.2–0.4 (ưu tiên 0.3) cho chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời nhất quán, chính xác và dễ kiểm soát, giảm rủi ro “bịa” hoặc trả lời lan man. Đồng thời vẫn giữ một chút linh hoạt để câu chữ tự nhiên, không quá cứng nhắc.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Đắt hơn 17 lần

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> Trường hợp chi phí cao hơn của GPT-4o là xứng đáng: khi xử lý tác vụ rủi ro cao cần độ chính xác và suy luận tốt (chính sách bảo hiểm)
- Trường hợp GPT-4o-mini tốt hơn: các tác vụ khối lượng lớn, lặp lại, yêu cầu phản hồi nhanh và “đủ tốt” (FAQ)

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các tình huống người dùng đang chờ trực tiếp và cần cảm giác phản hồi ngay, như chatbot hỗ trợ khách hàng, trợ lý viết nội dung, hoặc ứng dụng hỏi đáp thời gian thực, vì việc thấy từng phần câu trả lời xuất hiện sớm giúp giảm cảm giác chờ đợi và cải thiện trải nghiệm. Ngược lại, non-streaming phù hợp hơn khi cần câu trả lời hoàn chỉnh mới xử lý tiếp, ví dụ gọi API theo lô, tạo báo cáo/tóm tắt để lưu database, hoặc khi giao diện chỉ hiển thị kết quả cuối cùng; lúc này non-streaming đơn giản hơn trong xử lý lỗi, kiểm thử và kiểm soát đầu ra.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
