# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00-1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:

```bash
python template.py
```

Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00-1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature

Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2-3 câu)
> Khi temperature thấp như 0.0, câu trả lời thường ổn định, ngắn gọn và ít thay đổi giữa các lần gọi. Khi tăng lên 1.0 hoặc 1.5, mô hình có xu hướng sáng tạo hơn, cách diễn đạt đa dạng hơn nhưng cũng dễ thêm chi tiết không cần thiết hoặc kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> temperature khoảng 0.2 đến 0.5. Mức này giúp câu trả lời đủ tự nhiên nhưng vẫn ưu tiên tính chính xác, ổn định và nhất quán, đặc biệt khi trả lời chính sách, hướng dẫn hoặc thông tin sản phẩm.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí

Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload có 10.000 x 3 x 350 = 10.500.000 token mỗi ngày. Theo bảng giá, GPT-4o đắt hơn GPT-4o-mini khoảng 33,3 lần cho cả input token và output token, nên với cùng lượng token thì chi phí GPT-4o cũng cao hơn khoảng 33,3 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi tác vụ cần suy luận tốt hơn, độ chính xác cao hơn hoặc ảnh hưởng lớn đến trải nghiệm người dùng, ví dụ phân tích yêu cầu phức tạp, tư vấn kỹ thuật, hoặc xử lý tình huống nhạy cảm. GPT-4o-mini phù hợp hơn cho các tác vụ số lượng lớn, lặp lại và rủi ro thấp hơn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming

**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác hệ thống đang xử lý ngay lập tức, ví dụ chatbot tư vấn, viết nội dung dài, giải thích từng bước hoặc trợ lý lập trình. Việc hiển thị từng phần giúp giảm cảm giác phải chờ và cho phép người dùng đọc trước khi câu trả lời hoàn tất. Non-streaming phù hợp hơn khi phản hồi ngắn, cần xử lý kết quả hoàn chỉnh trước khi hiển thị, hoặc khi hệ thống cần kiểm duyệt nội dung trước rồi mới trả về cho người dùng.

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
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
