# GreenLane (Làn Xanh): Project Brief

## 1. Tóm tắt một câu

GreenLane biến xe giao hàng và xe công nghệ thành mạng cảm biến di động đo bụi mịn theo từng con đường, rồi đưa dữ liệu đó vào một ứng dụng giúp người dân chọn tuyến sạch và mát hơn, chỉ chậm thêm vài phút.

- **Tên:** GreenLane (Làn Xanh). Dòng phụ: *Urban Air Quality & Clean Routes*
- **Tagline:** *Every ride, data insight*
- **Cuộc thi:** UII Sandbox 2026, UEH. 

## 2. Vấn đề

- Dữ liệu chất lượng không khí hiện chỉ có theo **khu vực** và **thời điểm**. Người dân không biết con đường mình đi hoặc giờ mình đi có sạch hay không.
- Trạm quan trắc cố định thưa. Người dùng không có công cụ để tự bảo vệ sức khỏe ở cấp đường phố.
- Bằng chứng nhu cầu:
  - PM2.5 trung bình TP.HCM năm 2024 là 20,9 µg/m³ (IQAir), gấp hơn 4 lần mức 5 µg/m³ WHO khuyến nghị.
  - Khoảng 400.000 xe của tài xế công nghệ và giao hàng tại TP.HCM đang di chuyển mỗi ngày nhưng chưa được tận dụng làm mạng cảm biến (Người Quan Sát).
  - Pitch deck còn trích Hà Nội 45,9 µg/m³ (2025) và hơn 70.000 ca tử vong/năm liên quan ô nhiễm (WHO, 2026). **[Chưa kiểm chứng]**

## 3. Giải pháp

**Phần cứng:** node nhỏ gắn trên xe giao hàng gồm cảm biến bụi PMS7003, nhiệt độ/độ ẩm BME280, ESP32, GPS, module 4G và thẻ SD, lấy điện từ xe (12V hạ xuống 5V). Tài xế không phải thao tác.

**Luồng dữ liệu:** đo mỗi giây, ghi đệm vào thẻ SD, gửi lô mỗi 15–30 giây qua 4G (MQTT, mã hóa), mất sóng thì gửi bù. Thành phố chia thành ô lưới **50 m** theo khung giờ. Ô chỉ gắn nhãn "đo thật" khi có ít nhất 3 lượt đo từ 2 xe khác nhau, còn lại là "ước tính". Dữ liệu ẩn danh theo ô.

**Ứng dụng (iOS/Android):**
1. Bản đồ bụi cấp đường phố, xem theo giờ
2. Gợi ý 2–3 tuyến với thanh trượt "Nhanh hơn ↔ Sạch hơn"
3. Cảnh báo cá nhân theo tuyến quen, chế độ cho người nhạy cảm (trẻ em, người già, người bị hen)
4. Điểm xanh, huy hiệu và báo cáo lượng bụi đã tránh (không hiển thị vị trí)

**USP:** ứng dụng dẫn đường đầu tiên tại Việt Nam dùng dữ liệu bụi mịn đo thật cấp đường phố từ cảm biến gắn trên xe giao hàng.

## 4. Mô hình kinh doanh

- **Liên kết, không bán** thiết bị cho Grab, Xanh SM, Be: hãng phát thiết bị cho tài xế của mình, GreenLane cấp thiết bị và hỗ trợ lắp.
- Hãng nhận dashboard dữ liệu cho báo cáo ESG và cảnh báo AQI cho tài xế. Tài xế nhận cảnh báo và điểm xanh.
- **Lợi nhuận đến từ ứng dụng B2C** (freemium):
  - Miễn phí: bản đồ, gợi ý tuyến, thanh trượt.
  - Premium **[Giả định]** 30.000 đ/tháng: cảnh báo theo lịch trình, chế độ người nhạy cảm, báo cáo bụi đã tránh.
- B2B/B2G (ESG, bất động sản, bảo hiểm, cơ quan quản lý) là hướng giai đoạn sau, khi dữ liệu đủ dày và đáng tin.

## 5. Khách hàng mục tiêu

Phân khúc chính: **người quan tâm sức khỏe tại TP.HCM và Hà Nội, đi lại bằng xe cá nhân**.

| Persona | Mô tả | Nhu cầu cốt lõi |
|---|---|---|
| Hoàng Anh (nhóm 2) | 27 tuổi, kĩ sư khoa học dữ liệu, ≈20 triệu/tháng, đi xe máy ≈20 km/ngày, dùng Strava, Apple Watch | Chọn đường sạch/mát, thấy số bụi đã tránh, được ghi nhận là người sống xanh, ngại lộ vị trí |
| Chị Tuyến (nhóm 3) | 35 tuổi, nhân viên ngân hàng, hộ ≥35 triệu/tháng, con gái 6 tuổi | Cảnh báo tức thời, lộ trình đưa đón né bụi, lời khuyên cho trẻ, số liệu đáng tin |

Chưa ưu tiên ở giai đoạn này: tài xế/shipper (là bên cung cấp dữ liệu), doanh nghiệp và cơ quan quản lý.

## 6. Quy mô thị trường

| | TAM | SAM | SOM (12 tháng đầu) |
|---|---|---|---|
| **Top Down** (VNĐ/năm) | 117,4 tỷ | 2,93 tỷ | 46,0 triệu |
| **Bottom Up** (VNĐ/năm) | 137,6 tỷ | 19,1 tỷ | 119,9 triệu |
| Số người dùng | 18,2 triệu | 2,53 triệu | ≈15.857 (333 trả phí) |

- Phạm vi: Hà Nội + TP.HCM (địa giới cũ); năm 1 chỉ triển khai TP.HCM.
- Năm 1: 2.400 thiết bị ≈ 24% độ phủ TP.HCM (giả định cần 10.000 thiết bị để phủ đủ dày).
- **Lưu ý:** doanh thu thuê bao B2C rất nhỏ vì app sức khỏe Việt Nam thu chỉ ≈US$0,23 mỗi lượt tải (Statista). Giá trị lớn hơn nằm ở tập người dùng và dữ liệu.
- **Giả định chưa có nguồn:** giá 30.000đ; 35% lao động dịch vụ thuộc tuổi 22–38 và đại học trở lên; 85% đi xe cá nhân; 30% tài xế thuộc đối tác pilot; 2% gắn thiết bị; 10.000 thiết bị phủ đủ; 5% tải app; 3% thị phần.

## 7. Cạnh tranh và môi trường

- **Gián tiếp:** IQAir AirVisual (tải miễn phí, chỉ số theo khu vực), PAM Air (hơn 400 trạm cố định), mạng trạm quan trắc quốc gia.
- **Nghiên cứu/quốc tế:** Google Air View + Aclima, cảm biến trên taxi (Thượng Hải, Mỹ). Chưa thành sản phẩm cho người dùng cuối.
- **Porter:** rào cản thật là mạng lưới thiết bị và quan hệ với hãng xe; sản phẩm thay thế mức cao (app AQI miễn phí, khẩu trang, máy lọc khí).
- **PESTEL:** rủi ro pháp lý về dữ liệu vị trí (cần đồng ý rõ ràng và ẩn danh hóa), chính sách net-zero 2050 là thuận lợi.

## 8. Giả thuyết ưu tiên cần kiểm chứng

| # | Giả thuyết | Cách kiểm chứng | Ngưỡng đạt |
|---|---|---|---|
| 1 | Hãng xe sẵn sàng pilot 3 tháng nếu không phải trả phí thiết bị | Phỏng vấn 5 đại diện, xin LOI | ≥ 2/5 đồng ý, ≥ 1 LOI |
| 2 | Tài xế giữ thiết bị hoạt động | Thử ~20 tài xế trong 2 tuần | ≥ 80% giữ thiết bị |
| 3 | Cảm biến trên xe đủ chính xác | 5 node song song với trạm chuẩn | MAE ≤ 15% |
| 4 | Người dùng chọn tuyến sạch hơn nếu chậm thêm ≤ 5 phút | Usability test Figma ~50 người | ≥ 60% chọn tuyến sạch hơn |
| 5 | Sẵn sàng trả phí Premium | Khảo sát + fake-door pre-order | ≥ 20% sẵn sàng; chuyển đổi thực tế ≥ 2,1% |

## 9. Phạm vi MVP

- **Làm:** TP.HCM; pilot với một hãng xe công nghệ; 4 nhóm tính năng lõi (bản đồ bụi, gợi ý tuyến, cảnh báo cá nhân, điểm xanh).
- **Chưa làm:** bán dữ liệu B2B/B2G, mở rộng Hà Nội, quảng cáo.

## 10. Rủi ro chính

1. **Phụ thuộc đối tác:** không có hãng xe chịu gắn thiết bị thì không có dữ liệu, không có dữ liệu thì không có người dùng.
2. **Độ chính xác cảm biến** trên xe đang chạy (rung, nhiệt, độ ẩm).
3. **Quyền riêng tư vị trí:** cần ẩn danh theo ô 50 m, đồng ý rõ ràng, nhãn "đo thật/ước tính", không thay thế tư vấn y tế.
4. **Mức sẵn sàng trả phí thấp**, doanh thu thuê bao B2C nhỏ nên cần kiểm chứng nguồn thu khác.
5. **Lợi thế dễ thu hẹp** nếu thị trường được chứng minh (phần cứng rẻ, app dễ sao chép).

## 11. Trạng thái hiện tại

- Đã có: slide từ cover đến Value Proposition Canvas (19 slide), file Excel market sizing, persona, empathy map.
- **Còn thiếu cho Final Pitch Deck:** Research & MVP Development Plan, Team structure, Call to Action (tùy chọn). Final Pitch Deck yêu cầu ~15–20 slide; bản hiện tại đã gần chạm trần.
- Demo File (ảnh hoặc video minh họa MVP) nộp riêng.

## 12. Việc cần sửa trong deck hiện tại

- Tagline "date insight" nên là "data insight".
- Slide ứng dụng ghi "chị Lan", nhưng persona là "Chị Tuyến".
- Slide MVP còn "[điền giá] đồng/thiết bị" và "PM57003" (đúng là PMS7003).
- Slide Cơ hội thị trường: "20,8 µg/m²" (đúng là µg/m³; nguồn IQAir ghi 20,9), "ADI" (đúng là AQI), "2.400 triệt bị nằm 1" và một số chữ bị lỗi.
- Số liệu "70.000+ ca tử vong" và Hà Nội 45,9 µg/m³ chưa có link nguồn.

## 13. Nguồn dữ liệu chính

- Dân số: [NSO, điều tra giữa kỳ 2024](https://www.nso.gov.vn/wp-content/uploads/2025/01/Thong-cao-bao-chi-Ket-qua-chu-yeu-DSGK2024.pdf)
- Internet 84,2%: [DataReportal 2026](https://datareportal.com/reports/digital-2026-vietnam)
- 400.000 xe tại TP.HCM: [Người Quan Sát](https://nguoiquansat.vn/tp-hcm-muon-loai-dan-xe-xang-khoi-doi-ngu-tai-xe-grab-be-tu-nam-2026-225874.html)
- PM2.5 TP.HCM: [IQAir](https://www.iqair.com/newsroom/ho-chi-minh-city-among-the-most-polluted-cities-in-the-world-09-11-2025)
- Tỷ lệ trả phí freemium 2,1%: [RevenueCat 2026](https://www.revenuecat.com/blog/growth/subscription-app-trends-benchmarks-2026)
- Doanh thu app sức khỏe Việt Nam: [Statista](https://www.statista.com/outlook/amo/app/health-fitness/vietnam)
- Danh sách đầy đủ và link: file Excel, sheet "Nguồn dữ liệu"


