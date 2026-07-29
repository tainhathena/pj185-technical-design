# PJ185 — Proposal Technical Design v3.0

Bản đọc web của `docs/prd/PJ185_Technical_Design_v3.0.md` trong fork
`nocodb-smartsheet`. Thiết kế hub dữ liệu NocoDB đối chiếu Smartsheet
**Product Intake Sheet** với **PIM**.

→ https://tainhathena.github.io/pj185-technical-design/

## Nội dung

Một trang `index.html` duy nhất, sinh tự động từ Markdown. 42 mục, 24 bảng,
**14 sơ đồ Mermaid** — trong đó ERD đầy đủ trường ghi kèm hệ sở hữu và
fill-rate đo được của từng cột.

## Lưu ý khi đọc

- Nhãn ✅ = đã verify trên dữ liệu thật · ⚠️ = giả định · ❓ = chưa kiểm chứng.
  Đây là quy ước bắt buộc của tài liệu, không phải trang trí.
- Sơ đồ luôn nằm trên nền sáng ở cả hai chế độ màu, để Mermaid không phải
  render lại khi đổi theme. Nếu CDN Mermaid bị chặn, phần sơ đồ hiện nguyên
  văn mã nguồn thay vì hình — trang vẫn đọc được.
- Trang đặt `robots: noindex` vì tài liệu chứa dữ liệu nội bộ.

## Sinh lại trang

Trang này là output, không sửa tay. Sửa file Markdown gốc rồi build lại:

```bash
cd ~/pj185-site-build
node build.mjs ~/nocodb-smartsheet/docs/prd/PJ185_Technical_Design_v3.0.md ~/pj185-technical-design
```

`build.mjs` + `site.css` + `shell.html` nằm ở `~/pj185-site-build`
(markdown → HTML bằng `marked`; chỉ Mermaid chạy ở phía trình duyệt).
