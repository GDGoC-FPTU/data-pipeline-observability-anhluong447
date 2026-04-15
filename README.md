[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574005&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.anhlh2@vinuni.edu.vn
**Name:** Lương Hoàng Anh

---

## Mo ta

Bài lab này thực hiện xây dựng một Pipeline ETL (Extract, Transform, Load) tự động cho dữ liệu sản phẩm. Cụ thể:
- **Extract:** Đọc dữ liệu từ file JSON nguồn.
- **Validate:** Kiểm tra tính hợp lệ của dữ liệu (giá > 0, category không rỗng).
- **Transform:** Chuẩn hóa định dạng Category thành Title Case và tính toán giá sau chiết khấu 10%, thêm timestamp xử lý.
- **Load:** Lưu trữ kết quả đã làm sạch và biến đổi vào file CSV.

Ngoài ra, tôi cũng thực hiện Stress Test để so sánh phản ứng của AI Agent khi làm việc với dữ liệu "Sạch" và dữ liệu "Rác" để thấy được tầm quan trọng của Data Observability trong việc ngăn chặn các recommendation sai lệch.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# B1: Tao du lieu rac
python generate_garbage.py

# B2: Chay mo phong so sanh behavior giua processed_data.csv va garbage_data.csv
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Pipeline ETL:** Hoạt động ổn định, xử lý 5 bản ghi đầu vào, lọc bỏ 2 bản ghi lỗi (1 bản ghi giá âm, 1 bản ghi thiếu category), lưu thành công 3 bản ghi sạch.
- **Stress Test:** Chứng minh được rằng nếu không có Data Validation, AI Agent sẽ bị "độc hóa" (data poisoning) và đưa ra các khuyến nghị phi lý (như đề xuất mua Lò phản ứng hạt nhân thay vì Laptop).
- **Bài học:** Chất lượng dữ liệu quan trọng hơn chất lượng câu lệnh (Data Quality > Prompt Quality). Quan sát dữ liệu là chìa khóa để AI hoạt động tin cậy.
