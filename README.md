# PJ185 — Proposal Technical Design

Bản đọc web của `docs/prd/PJ185_Technical_Design_*.md` trong fork
`nocodb-smartsheet`. Thiết kế hub dữ liệu NocoDB đối chiếu Smartsheet
**Product Intake Sheet** với **PIM**.

→ https://tainhathena.github.io/pj185-technical-design/

## Các bản

| Trang | Bản | Ngày | Trạng thái |
|---|---|---|---|
| [`/`](https://tainhathena.github.io/pj185-technical-design/) hoặc [`/v3-1.html`](https://tainhathena.github.io/pj185-technical-design/v3-1.html) | **v3.1** | 2026-07-31 | **mới nhất** — 43 mục, 29 bảng, 14 sơ đồ |
| [`/v3.html`](https://tainhathena.github.io/pj185-technical-design/v3.html) | v3.0 | 2026-07-29 | đã thay thế — thiếu kết quả pull 31-07 (D-01, luật N6, 2 số đếm sai) |

`/` luôn trỏ bản mới nhất; mỗi bản còn giữ URL cố định `vN.html` để trích dẫn
được một bản cụ thể. Trang cũ mở đầu bằng một banner nói rõ nó sai ở đâu.

**v1.0 và v2.0 đã bỏ khỏi site** (2026-07-31) — hai bản đó sai mô hình dữ liệu
ở mức không nên để người ngoài đọc: v1.0 tính số trên export PIM bị cắt còn
145/390 dòng, v2.0 vẽ ERD với `Groups` là cha của `Teams` và `product_code` là
khoá duy nhất. Chỉ giữ v3.0 vì bản nháp đó đang lưu hành chờ ký. Markdown gốc
của v1.0/v2.0 vẫn nằm trong `docs/prd/` của repo `nocodb-smartsheet` nếu cần
tra lịch sử; muốn xuất bản lại thì thêm mục vào `versions.json` là đủ.

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
