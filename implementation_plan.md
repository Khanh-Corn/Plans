# Kế Hoạch Phát Triển Dự Án: Tu Tiên Origin (2D Side-Scrolling RPG)

Dự án này là một game nhập vai tu tiên 2D màn hình ngang dành cho Android và Windows, tập trung vào trải nghiệm cày cuốc, thăng cấp cảnh giới và chiến đấu kỹ năng.

---

## 1. Môi trường phát triển (Setup)
- **Game Engine**: Unity 2022.3 LTS (Sử dụng 2D Core Template).
- **Backend**: XAMPP (Apache, MySQL) để quản lý tài khoản và dữ liệu nhân vật.
- **Ngôn ngữ**: C# (Unity) và PHP (API/Backend).
- **Công cụ hỗ trợ**:
    - **Unity 2D Animation Package**: Để gắn xương (Rigging) cho nhân vật Chibi.
    - **Postman**: Để kiểm tra các API kết nối Database.

---

## 2. Thiết kế Cơ sở dữ liệu (Database)
Hệ thống cần các bảng chính sau (đã có file `backend/database.sql`):
- `users`: Quản lý tài khoản và mật khẩu.
- `characters`: Lưu chỉ số (Máu, Dame, Giáp, Tốc độ, Mana), Cảnh giới (Luyện Khí -> ... -> Nguyên Anh), và Tiên Ngọc.
- `inventory`: Lưu trang bị và pháp bảo của từng nhân vật.
- `skills`: Danh sách thần thông và cấp độ của chúng.

---

## 3. Hệ thống Hình ảnh & Animation
Sử dụng phong cách **Chibi 2D** để tối ưu hiệu suất Mobile.

### Phương pháp Animation kiến nghị: **Skeletal Animation (Hoạt họa xương)**
- **Tài nguyên**: Sử dụng các bộ phận đã tách rời (`head.png`, `torso.png`, `arms.png`, `legs.png`) trong thư mục `simulation/assets/luyen_the_parts/`.
- **Thực hiện**:
    1. Import các bộ phận vào Unity.
    2. Sử dụng **Sprite Editor** -> **Skinning Editor** để tạo xương (Bones).
    3. Tạo các Clip Animation: `Idle`, `Walk`, `Run`, `Attack_1`, `Attack_2`, `Skill`.

---

## 4. Cơ chế Gameplay cốt lõi
### Phân chia Class:
1. **Luyện Thể (Võ Tu)**: 
    - Đánh tay cực nhanh, mạnh.
    - Sử dụng Thể lực thay vì Mana.
    - Kỹ năng thiên về áp sát, khống chế và "Bá Thể".
2. **Luyện Khí (Pháp Tu)**:
    - Dame cực to, diện rộng.
    - Tốn nhiều Mana, hồi chiêu lâu.
    - Cần di chuyển (Hit & Run) để tránh bị tiếp cận.

### Hệ thống Thần thông (4 Slot + 1 Đánh thường):
- Người chơi có thể tự do thay đổi 4 thần thông mang theo tùy theo mục tiêu (Train quái hoặc Đánh Boss).
- **Chiến lực (CP)** = (Chỉ số cơ bản) + (Trang bị) + (Pháp bảo) + (Cấp độ Thần thông) + (Phẩm cấp Cảnh giới).

---

## 5. Lộ trình triển khai (Roadmap)

### Giai đoạn 1: Prototype (Tuần 1-2)
- Hoàn thiện di chuyển nhân vật (Move, Jump, Dash).
- Hoàn thiện hệ thống Combo đánh thường cơ bản.
- Thiết lập Map Tân Thủ (Thanh Vân Bang) với hiệu ứng Parallax.

### Giai đoạn 2: Hệ thống Tu luyện & Dữ liệu (Tuần 3-4)
- Viết API PHP để lưu/tải nhân vật từ Database MySQL.
- Code logic tăng EXP khi đánh quái và nút **"Đột Phá"** cảnh giới.
- Xây dựng Inventory (Túi đồ) cơ bản.

### Giai đoạn 3: Chiến đấu & Boss (Tuần 5-6)
- Thiết kế AI cho quái vật (Tuần tra, Đuổi theo người chơi).
- Xây dựng hệ thống Boss thế giới với tỉ lệ rơi Pháp bảo hiếm.
- Hoàn thiện 4 kỹ năng đặc trưng cho mỗi hệ.

### Giai đoạn 4: Đóng gói & Phát hành (Tuần 7-8)
- Thiết kế UI/HUD hoàn chỉnh (Thanh máu, Mana, Icon kỹ năng).
- Tối ưu hóa hiệu năng cho Android (Fix Frame Rate, giảm dung lượng ảnh).
- Build file `.apk` và `.exe`.

---

## 6. Các tài nguyên quan trọng đã tạo
Bạn có thể tìm thấy chúng trong thư mục dự án:
- **Ảnh Concept**: `landing/`, `visual_assets_preview.md`.
- **Sprite Sheets & Parts**: `simulation/assets/`.
- **Script Unity mẫu**: `client/Scripts/` (`PlayerController.cs`, `CultivationManager.cs`).
- **Database Schema**: `backend/database.sql`.

---
*Chúc bạn xây dựng được một thế giới Tu Tiên thật hoành tráng!*
