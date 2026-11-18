# Thông tin học viên

- Họ và tên: Phạm Văn Dương
- MSHV: 2A202603332
- Lớp (L2 / L3 / khác): L2B
- Tài khoản GitHub: pvd2201
- Repo bài nộp (URL): https://github.com/pvd2201/K5-L23-Day08-PhamVanDuong-2A202603332-AI-Assisted-Labeling
- Commit chốt bài (hash): 735df1f3c73d241be655bbf5099fc339adb56a21
- Máy: Windows 11; Intel Iris Xe và NVIDIA GeForce MX550 (2 GB). PyTorch trong `.venv` là bản CPU-only; các lần chạy đã ghi dùng CPU.
- CVAT (Docker): v2.81.0.

## Kết quả tóm tắt (điền cuối bài; số lấy từ `submission/qc/*`, kèm mẫu số)

- Máy: accepted / edited / deleted: 423/612 = 69,1% / 76/612 = 12,4% / 113/612 = 18,5%; added: 44/543 = 8,1%.
- So với gold: precision / recall của **máy** 43/83 = 51,8% / 43/51 = 84,3% (51 đối tượng gold được tính, không gồm ignore region).
- Bắt bẫy: 10/12 = 83,3%; lọt 2 bẫy loose.
- Thời gian: gán tay 30/4 = 7,5 phút/ảnh; duyệt có pre-label 70/24 ≈ 2,9 phút/ảnh.
- Lỗi QC: 0/5 ảnh = 0%; 0/100 đối tượng = 0%.
- **Quyết định:** Release (theo REPORT hiện tại); mẫu QC nhỏ, cận trên Wilson 95% là 43%.
