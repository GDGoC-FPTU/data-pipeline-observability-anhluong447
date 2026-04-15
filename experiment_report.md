# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600472
**Name:** Lương Hoàng Anh
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10 | The agent correctly identifies the best electronic product from clean data. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | The agent recommended a nuclear reactor as an 'electronic', which is a massive outlier and likely non-existent in a retail context. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi sử dụng dữ liệu rác (Garbage Data), Agent đưa ra kết quả sai lệch nghiêm trọng vì nó thiếu cơ chế tự kiểm chứng tính hợp lý của thông tin đầu vào. Trong thí nghiệm này, Agent đã đề xuất một "Nuclear Reactor" với giá cực lớn ($999999) chỉ vì nó được gắn nhãn là "electronics".

Các vấn đề cụ thể bao gồm:
- **Outliers (Giá trị ngoại lai):** Bản ghi Nuclear Reactor có giá quá cao so với các sản phẩm điện tử thông thường, làm sai lệch logic tìm kiếm "best choice".
- **Wrong Data Types:** Nếu dữ liệu giá là chuỗi ("ten dollars"), Agent có thể bị lỗi khi so sánh hoặc tính toán.
- **Duplicate IDs/Null values:** Gây nhiễu quá trình truy vấn và làm mất độ tin cậy của báo cáo.
Dữ liệu không được làm sạch dẫn đến hiện tượng "Garbage In, Garbage Out", làm cho Agent đưa ra những tư vấn vô nghĩa hoặc thậm chí nguy hiểm.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Tôi hoàn toàn đồng ý. Dù prompt có hay đến đâu, nếu dữ liệu nền tảng bị sai lệch, thiếu sót hoặc chứa mã độc (data poisoning), AI sẽ luôn đưa ra kết quả không chính xác. Quan sát và kiểm soát chất lượng dữ liệu (Data Observability) là bước tối quan trọng để xây dựng các hệ thống AI tin cậy trong thực tế.
