# Số đo review (det)

- Ảnh tính: 24 (batch,gold); box máy: 612; đối tượng sau duyệt: 543; ngưỡng accepted: IoU >= 0.9
- Đã **loại 22 đối tượng nằm quanh các bẫy** khỏi bảng này: lỗi nhân tạo không phản ánh chất lượng máy.

## 1. Bốn trạng thái (AI error profile)
| Trạng thái | Số | Tỉ lệ | Mẫu số |
|---|---|---|---|
| accepted (giữ nguyên) | 423 | 423/612 = 69.1% | 612 box máy |
| edited (sửa) | 76 | 76/612 = 12.4% | 612 box máy |
| deleted (xoá) | 113 | 113/612 = 18.5% | 612 box máy |
| added (vẽ thêm) | 44 | 44/543 = 8.1% | 543 đối tượng sau duyệt |

Trong số deleted + added, **13 trường hợp là đổi lớp** (máy gán sai lớp, box đúng chỗ): đó không phải máy bỏ sót. Số vật máy **sót thật** ≈ added − đổi lớp = 31.

### Theo lớp
| Lớp | accepted | edited | deleted | added |
|---|---|---|---|---|
| person | 239 | 16 | 16 | 16 |
| bicycle | 5 | 2 | 5 | 4 |
| motorbike | 126 | 44 | 68 | 8 |
| car | 42 | 7 | 6 | 3 |
| bus | 3 | 0 | 0 | 5 |
| truck | 1 | 0 | 6 | 1 |
| three_wheeler | 7 | 7 | 12 | 7 |

## 2. So với gold (nhãn gán tay từ đầu)
Ảnh gold: 4; đối tượng gold: 51 (mẫu số của recall)
| | TP | FP | FN | Precision | Recall |
|---|---|---|---|---|---|
| Máy (pre-label) | 43 | 40 | 8 | 51.8% (KTC 95%: 41–62%) | 84.3% (KTC 95%: 72–92%) |

*Lạc quan: ngưỡng được chọn trên chính các ảnh gold này (in-sample), và chỉ có 4 ảnh. Đọc khoảng tin cậy, đừng đọc con số đơn.*


(Ảnh gold không nằm trong nhãn sau duyệt: không tính residual / new error. Đó là chủ ý: duyệt lại ảnh bạn vừa tự gán tay sẽ đo trí nhớ, không đo thiên kiến.)

## 3. Ảnh bẫy
- Bắt được 10/12 = 83.3% (KTC 95%: 55–95%) (ngưỡng đạt: 80%). Chỉ 12 bẫy nên khoảng tin cậy rất rộng: đọc cùng danh sách bẫy lọt, đừng kết luận chỉ từ %.
  - missing: 3/3
  - extra: 3/3
  - loose: 1/3
  - wrong_class: 3/3
  - lọt: img_029.jpg (loose), img_026.jpg (loose)

## Gợi ý đọc số
- `deleted` cao → ngưỡng thấp hoặc ánh xạ nhãn sai; `added` cao → máy bỏ sót (xem lớp nào);
- `accepted` thấp (< 50%) → sửa mỗi box lâu hơn vẽ mới: đổi model/ngưỡng hoặc vẽ tay;
- bắt bẫy < 80% → duyệt lại lô, siết checklist (quét ảnh TRƯỚC khi nhìn nhãn máy).
