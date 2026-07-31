# PJ185 — Proposal Technical Design

Bản đọc web của `docs/prd/PJ185_Technical_Design_*.md` trong fork
`nocodb-smartsheet`. Thiết kế hub dữ liệu NocoDB đối chiếu Smartsheet
**Product Intake Sheet** với **PIM**.

→ https://tainhathena.github.io/pj185-technical-design/

## Các bản

| Trang | Bản | Ngày | Trạng thái |
|---|---|---|---|
| [`/`](https://tainhathena.github.io/pj185-technical-design/) hoặc [`/v3.html`](https://tainhathena.github.io/pj185-technical-design/v3.html) | **v3.0** | 2026-07-29 | mới nhất — 42 mục, 24 bảng, **14 sơ đồ** |
| [`/v2.html`](https://tainhathena.github.io/pj185-technical-design/v2.html) | v2.0 | 2026-07-29 | đã thay thế — ERD có 3 lỗi mô hình |
| [`/v1.html`](https://tainhathena.github.io/pj185-technical-design/v1.html) | v1.0 | 2026-07-27 | đã thay thế — số liệu sai do export PIM bị cắt |

`/` luôn trỏ bản mới nhất; mỗi bản còn giữ URL cố định `vN.html` để trích dẫn
được một bản cụ thể. Bản cũ vẫn công khai để tra lịch sử quyết định, và mỗi
trang cũ mở đầu bằng một banner nói rõ nó sai ở đâu.

## Lưu ý khi đọc

- Nhãn ✅ = đã verify trên dữ liệu thật · ⚠️ = giả định · ❓ = chưa kiểm chứng.
  Đây là quy ước bắt buộc của tài liệu, không phải trang trí.
- Sơ đồ luôn nằm trên nền sáng ở cả hai chế độ màu, để Mermaid không phải
  render lại khi đổi theme. Nếu CDN Mermaid bị chặn, phần sơ đồ hiện nguyên
  văn mã nguồn thay vì hình — trang vẫn đọc được.
- Trang đặt `robots: noindex` vì tài liệu chứa dữ liệu nội bộ.

## Sinh lại trang

Các trang này là output, không sửa tay. Sửa file Markdown gốc rồi build lại —
một lệnh sinh cả ba bản cùng lúc:

```bash
cd ~/pj185-site-build
node build.mjs versions.json ~/pj185-technical-design
```

`build.mjs` + `site.css` + `shell.html` + `versions.json` nằm ở
`~/pj185-site-build` (markdown → HTML bằng `marked`; chỉ Mermaid chạy ở phía
trình duyệt). Thêm một bản mới = thêm một mục vào `versions.json` và đổi
`status` của bản cũ thành `superseded`.
