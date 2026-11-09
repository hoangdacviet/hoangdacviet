# Kome Design V1

Ngôn ngữ thiết kế chung cho Kome Studio / Komeverse và các sản phẩm Kome. Xem bản trực quan tại `KomeDesignV1.html`.

> **Nguyên tắc cốt lõi: "Hình khối cơ bản, màu nguyên bản, lõi đặc, rìa kính."**
> Mọi thứ xuất phát từ logo: hình tròn, bán nguyên, góc phần tư, ba màu chính vàng - đỏ - xanh, chỗ giao nhau tạo màu mới.

## 1. Nguồn gốc từ logo

| Yếu tố logo | Áp dụng vào UI |
|---|---|
| Hình tròn, bán nguyên, góc phần tư | Bo góc lớn, avatar tròn, nút tròn, trang trí nền bằng hình khối |
| Màu phẳng, không gradient | Nền màu đặc, không dùng gradient để trang trí |
| Vàng chồng xanh ra đỏ | Điểm nhấn "giao nhau" cho hero, empty state, loading |
| Mắt chấm tròn trong chữ "e" | Linh vật, chấm trạng thái, thông báo có nhân vật |

## 2. Màu

### Màu thương hiệu (lấy từ logo)
| Tên | Hex | Vai trò |
|---|---|---|
| Kome Yellow | `#FFC90E` | **Hành động chính** (nút Primary), nhấn mạnh |
| Kome Red | `#F34040` | Hình khối, cảnh báo, nhấn thương hiệu |
| Kome Blue | `#4488FF` | Liên kết, thông tin, hình khối |
| Kome Gold | `#FABB05` | Hover/pressed của vàng, huy hiệu |

### Màu chữ-trên-nền (đạt tương phản AA)
| Tên | Hex | Dùng khi |
|---|---|---|
| Blue 600 | `#2D6BE4` | Nền nút/chữ xanh với chữ trắng |
| Red 600 | `#D92D2D` | Nền nút/chữ đỏ với chữ trắng |
| Green 600 | `#148046` | Thành công |
| Ink | `#1A1B2E` | Chữ chính, chữ trên nền vàng |

### Trung tính
| | Sáng | Tối |
|---|---|---|
| Nền (L0) | `#F6F7FB` | `#14151F` |
| Bề mặt (L1) | `#FFFFFF` | `#1E2030` |
| Viền | `#E3E5EE` | `#33364A` |
| Chữ phụ | `#5B5F76` | `#A9ADC4` |

**Quy tắc:** 70% trung tính, 20% một màu thương hiệu, 10% màu còn lại. Mỗi màn hình có **một** hành động chính màu vàng. Không dùng chữ trắng trên `#FFC90E`, `#4488FF`, `#F34040` (không đủ tương phản), hãy dùng bản 600 hoặc chữ Ink.

## 3. Chữ

- Font: **Be Vietnam Pro** (hỗ trợ tiếng Việt đầy đủ), dự phòng `Inter, system-ui, sans-serif`.
- Thang: 12 / 14 / 16 / 20 / 24 / 32 / 48 / 64.
- Đậm: 400 (nội dung), 600 (nhãn, nút), 800 (tiêu đề).
- Độ dài dòng ≤ 70 ký tự. Viết hoa chữ đầu câu, không viết hoa toàn bộ.

## 4. Hình khối, độ cao, khoảng cách

- **Bo góc:** `8` chip/input nhỏ, `16` input/nút, `24` card, `32` sheet/dialog, `999` nút tròn, avatar.
- **Góc đặc trưng (Kome corner):** card nổi bật có một góc bo `4px` còn ba góc bo lớn, gợi hình góc phần tư của logo.
- **Lưới:** bội số của 4 (4, 8, 12, 16, 24, 32, 48, 64).
- **Độ cao 3 tầng:**
  - L0: nền trang, phẳng.
  - L1: card, bề mặt đặc, viền 1px, bóng nhẹ.
  - L2: lớp nổi (nav, sheet, toolbar), dùng **Kome Glass**.

### Kome Glass
- Blur 24px, saturate 160%, nền bề mặt 60-70%, viền sáng 1px, highlight trên cùng.
- Chỉ dùng cho lớp nổi, tối đa 2 lớp kính chồng nhau, không dùng cho khối nội dung chính.
- Bắt buộc có **fallback đặc** khi không hỗ trợ `backdrop-filter` hoặc người dùng bật giảm trong suốt.

## 5. Chuyển động

- Thời gian: 150ms (nhấn nút), 250ms (đổi trạng thái), 400ms (sheet, dialog).
- Easing: nảy nhẹ `cubic-bezier(.34,1.56,.64,1)` cho tương tác; `cubic-bezier(.2,0,0,1)` cho chuyển cảnh.
- Chuyển động chỉ để phản hồi hành động. Tôn trọng `prefers-reduced-motion`.

## 6. Component V1

| Component | Quy cách chính |
|---|---|
| Button | Primary (vàng, chữ Ink), Secondary (xanh 600), Outline, Text, Danger (đỏ 600). Cao 48px, bo 16. Nhấn: nhún `scale(.96)` |
| FAB / Icon button | Tròn 56 / 44px |
| Input / Select | Cao 48px, bo 16, viền 1.5px, focus viền xanh + vòng 3px |
| Checkbox / Radio / Switch | Vùng chạm ≥ 44px, chọn = nền xanh 600 |
| Slider | Rãnh 8px, núm tròn 24px |
| Chip / Badge | Bo tròn, cao 32px; badge dùng màu thương hiệu + chữ Ink |
| Tabs / Segmented | Chỉ báo dạng viên thuốc trượt |
| Card | L1, bo 24, tuỳ chọn Kome corner |
| List item | Cao ≥ 56px, avatar tròn bên trái |
| Alert / Toast | Có biểu tượng + nội dung nói rõ chuyện gì xảy ra và cách xử lý |
| Dialog / Sheet | L2 kính + lớp phủ tối 40%, bo 32 |
| Tooltip | Nền Ink, chữ trắng, bo 8 |
| Progress | Thanh dày 12px bo tròn, chạy có độ nảy (kiểu game) |
| Bottom nav | Kính, mục đang chọn là viên thuốc vàng |

## 7. Trợ năng (bắt buộc)
1. Tương phản chữ ≥ 4.5:1 (chữ lớn ≥ 3:1), kiểm tra cả trên nền kính.
2. Vùng chạm ≥ 44x44px (ưu tiên 48px).
3. Focus rõ: viền xanh 3px, cách 2px, không bao giờ `outline: none`.
4. Không dùng màu làm tín hiệu duy nhất, luôn kèm biểu tượng hoặc chữ.
5. Theme có 3 chế độ: ☀️ Light, 🌙 Dark, 🌗 Auto (mặc định, theo thiết bị). Hỗ trợ dark mode, `prefers-reduced-motion`, `prefers-reduced-transparency`.

## 8. Văn phong
- Câu ngắn, động từ rõ ràng: "Lưu thay đổi", không viết "Gửi".
- Lỗi: nói chuyện gì xảy ra + cách sửa, không xin lỗi chung chung.
- Trạng thái trống: mời người dùng làm bước tiếp theo.

## 9. Nên và không nên
- **Nên:** nền phẳng, hình khối lớn, một điểm nhấn mỗi màn hình, chữ Ink trên nền vàng.
- **Không:** gradient trang trí, kính cho khối nội dung, chữ trắng trên vàng, hơn 2 lớp kính, hơn 1 nút vàng mỗi màn hình.

## 10. CSS token (sao chép dùng ngay)

```css
:root {
  --k-yellow:#FFC90E; --k-gold:#FABB05; --k-red:#F34040; --k-blue:#4488FF;
  --k-blue-600:#2D6BE4; --k-red-600:#D92D2D; --k-green-600:#148046;
  --k-ink:#1A1B2E; --k-on-yellow:#1A1B2E; --k-bg:#F6F7FB; --k-surface:#FFFFFF;
  --k-border:#E3E5EE; --k-muted:#5B5F76;
  --k-r-sm:8px; --k-r-md:16px; --k-r-lg:24px; --k-r-xl:32px;
  --k-spring:cubic-bezier(.34,1.56,.64,1); --k-ease:cubic-bezier(.2,0,0,1);
  --k-font:"Be Vietnam Pro",Inter,system-ui,sans-serif;
}
:root[data-theme="dark"] {
  --k-bg:#14151F; --k-surface:#1E2030; --k-border:#33364A; --k-muted:#A9ADC4; --k-ink:#F3F4FA;
}
```

## 11. Quy trình áp dụng
1. Copy khối token ở mục 10 vào dự án (hoặc Tailwind preset tương ứng).
2. Dựng component theo mục 6, đối chiếu với `KomeDesignV1.html`.
3. Chạy checklist mục 7 trước khi phát hành.

*Phiên bản: V1.0*
