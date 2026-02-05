# Network Intrusion Detection System (IDS) based on Decision Tree

## 📌 Giới thiệu (Introduction)
Dự án này nghiên cứu và xây dựng một hệ thống phát hiện xâm nhập mạng (Intrusion Detection System - IDS) sử dụng các kỹ thuật Học máy (Machine Learning). Hệ thống được huấn luyện trên bộ dữ liệu chuẩn **CIC-IDS2017** để phân loại lưu lượng mạng thành **Bình thường (Benign)** hoặc **Tấn công (Attack)**.

Trọng tâm của dự án là phát hiện 3 nhóm tấn công phổ biến nhất hiện nay:
1.  **Reconnaissance:** PortScan (Dò quét cổng).
2.  **Access:** Brute Force (Vét cạn mật khẩu SSH/FTP).
3.  **Disruption:** DDoS (Tấn công từ chối dịch vụ).

Sau quá trình thực nghiệm so sánh giữa Logistic Regression, Random Forest và Decision Tree, mô hình **Decision Tree** đã được lựa chọn làm giải pháp tối ưu nhờ khả năng cân bằng giữa độ chính xác và tốc độ xử lý.

## 📊 Kết quả nổi bật (Key Results)
Mô hình **Decision Tree** đạt hiệu suất ấn tượng trên tập kiểm thử tích hợp:
- **Độ chính xác (Accuracy):** 99.98%
- **Độ nhạy (Recall):** 99.98% (Chỉ bỏ lọt 2 mẫu tấn công trên tổng số 12,067 mẫu).
- **So sánh với Random Forest:** Decision Tree phát hiện tốt hơn (chỉ bỏ lọt 2 so với 11 của Random Forest) và có tốc độ dự đoán nhanh hơn, phù hợp cho triển khai thời gian thực.

## 📂 Cấu trúc dự án (Project Structure)
```text
├── Source_Code_IDS.ipynb        # File mã nguồn chính (Chạy trên Google Colab/Jupyter)
├── Source_Code_Script.py        # File mã nguồn định dạng Python Script
├── decision_tree_ids_model.joblib # Mô hình đã huấn luyện sẵn (Pre-trained model)
├── randorm_forest_ids_model.joblib # Mô hình đã huấn luyện sẵn (Pre-trained model)
├── requirements.txt             # Danh sách các thư viện cần thiết
└── README.md                    # Tài liệu hướng dẫn
```
## 💾 Dữ liệu (Dataset)
Dự án sử dụng bộ dữ liệu **CIC-IDS2017** từ Viện An ninh mạng Canada (CIC). Do chính sách bản quyền và kích thước file lớn, dữ liệu không được đính kèm trực tiếp trong repository này.

Vui lòng tải 3 file sau từ [Trang chủ CIC-IDS2017](https://www.unb.ca/cic/datasets/ids-2017.html) và đặt vào cùng thư mục với file code:
1.  `Friday-WorkingHours-Afternoon-PortScan.pcap_ISCX.csv`
2.  `Tuesday-WorkingHours.pcap_ISCX.csv`
3.  `Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv`

## 🚀 Hướng dẫn cài đặt & Chạy (Installation & Usage)

### Cách 1: Chạy trên Google Colab (Khuyên dùng)
1.  Tải file `Source_Code_IDS.ipynb` lên Google Colab.
2.  Upload 3 file dữ liệu `.csv` vào bộ nhớ tạm của Colab.
3.  Chọn **Runtime** -> **Run all** để huấn luyện và xem kết quả.

### Cách 2: Chạy trên máy cá nhân
**Bước 1: Clone dự án và cài đặt thư viện**
```bash
git clone [https://github.com/](https://github.com/)[Your-Username]/IDS-Project.git
cd IDS-Project
pip install -r requirements.txt
```
**Bước 2: Chạy chương trình huấn luyện**
```
python Source_Code_Script.py
```
**Bước 3: Sử dụng mô hình có sẵn (Không cần train lại) Bạn có thể sử dụng file decision_tree_ids_model.joblib để dự đoán dữ liệu mới bằng đoạn code sau:**
```
import joblib
# Tải mô hình
model = joblib.load('decision_tree_ids_model.joblib')
# Dự đoán
# prediction = model.predict(X_new_data)
```
