# Phiếu QC 1 — Road v1.0

Lô được kiểm · Nguyễn Viết Minh Hoàng  
Người kiểm · Nguyễn Văn Nhất 
Ngày · 20/11/2026  
Bản đã kiểm · nguyenvietminhhoang revision
Số ảnh kiểm · 6  
**Số nhãn đã kiểm** · 51 (27 shape và 24 tag)

## Tổng hợp theo mã

| Mã | Hạng mục | Số mục kiểm | Số lỗi xác nhận | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 | Camera | 6 | 0 | nặng |
| QC1-02 | Vị trí L1/R1 cần đối chiếu ảnh | 12 | 0 | nặng |
| QC1-03 | Position của lane | 13 | 0 | nặng |
| QC1-04 | Tâm vạch, chiều, điểm dừng | 13 | 3 | chính |
| QC1-05 | Vạch đứt, đoạn che | 13 | 0 | chính |
| QC1-06 | Style, color, kind | 13 | 0 | chính |
| QC1-07 | Drivable, crosswalk, road_curb | 14 | 2 | chính |
| QC1-08 | Đèn, màu | 0 | 0 | nặng / chính |
| QC1-09 | Facing, type, group, biển phụ | 0 | 0 | chính |
| QC1-10 | Hình in, đủ biển | 0 | 0 | chính |
| QC1-11 | Fisheye | 0 | 0 | chính |
| QC1-12 | Đọc lại XML của mẫu | 1 | 0 | nhẹ / nặng |


## Danh sách lỗi

| # | Mã | Ảnh | Nhãn | Mức | Bằng chứng và cách sửa |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A01 | `lane R2` | chính | Vạch vàng bên phải bị vẽ cao hơn tâm sơn. Ở x≈850, đường nhãn đi qua y≈590 còn tâm sơn ở y≈602. Kéo các điểm giữa xuống theo tâm vệt vàng. |
| 2 | QC1-04 | A02 | `lane R1` | chính | Đường liền bên phải lệch khỏi tâm đoạn giữa. Ở x≈800, đường nhãn ở y≈478 còn nét sơn ở khoảng y≈488–491. Rà lại đoạn x≈740–860. |
| 3 | QC1-04 | A03 | `lane L1` | chính | Polyline đi vào phía dải phân cách ở đoạn nét vàng tách ra. Ở y≈550, đường nhãn ở x≈362 còn nét vàng sát làn ở x≈374–380. Chỉnh đoạn này bám phần vạch thực sự là ranh làn. |
| 4 | QC1-07 | A04 | `drivable / alternative` | chính | Mép dưới polygon ăn vào dải capô màu xám ở nửa phải ảnh. Đưa mép polygon lên đường tiếp giáp mặt đường và capô. |
| 5 | QC1-07 | A06 | `crosswalk` | chính | Polygon dừng sớm bên phải cột sọc giữa ảnh, bỏ các nét trắng tiếp nối của vùng qua đường phía gần vỉa hè. Mở rộng đường bao qua các nét tiếp nối và dừng trước vỉa hè. |

Tọa độ minh họa lấy trên ảnh gốc 1280 × 720 để tìm nhanh vị trí chỉnh. Ngưỡng 5 px áp dụng cho độ lệch khỏi tâm vạch.

## Ca mơ hồ

| Ảnh | Câu hỏi | Nhận định khi chấm thử |
| --- | --- | --- |
| A05 | Hai bên làn có vạch L1/R1 nhìn thấy được không? | Không thấy vạch sơn phân làn đủ rõ. Hai cảnh báo lint QC1-02 chưa được tính là lỗi. Không ghi lỗi xác nhận khác trên ảnh này. |
| A06 | Nét sơn gần vỉa bên phải có phải R1 của làn xe đang đi không? | Nét thấy rõ thuộc vùng qua đường hoặc mép đường. Chưa thấy R1 đủ rõ. Cảnh báo lint QC1-02 chưa được tính là lỗi. |

## Quyết định

**Rework cho mẫu A01–A06.** Có 0 lỗi nặng đã xác nhận, 5 lỗi chính trên 51 nhãn (**9,8%**), 0 lỗi nhẹ đã xác nhận và 2 ca cần coach xác nhận. Tỉ lệ lỗi chính vượt 5%. Rà các vị trí trên bản CVAT hiện tại trước khi sửa vì bản hiện tại có thể đã được chỉnh sau khi import.
