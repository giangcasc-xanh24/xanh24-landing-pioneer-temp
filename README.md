# Xanh24 Landing V30 - Deploy hướng dẫn

## Cấu trúc folder (BẮT BUỘC cho Vercel):
```
xanh24-deploy/
├── index.html              <- Landing chính (V30)
├── Landing_Page_1_light.mp4 <- Video fallback (root)
├── public/
│   └── video/
│       └── pioneer-day.mp4 <- Video chính cho popup LIVE
└── logo.png
```

## Cách up lên GitHub (3 cách):

### Cách 1: GitHub Web (dễ nhất cho bạn)
1. Vào repo: https://github.com/xanh-24/xanh24-landing-pioneer-temp-hdr58orar-xanh-24
2. Bấm Add file -> Upload files
3. Kéo thả file index.html vào (ghi đè file cũ)
4. Bấm Add file -> Create new file
   - Tên file: public/video/pioneer-day.mp4 (gõ y nguyên, GitHub sẽ tự tạo folder)
   - GitHub web không upload được MP4 lớn >25MB qua web, nên dùng Cách 2
5. Nên dùng Cách 2 hoặc 3 cho video

### Cách 2: Dùng Git trên máy (khuyên dùng)
```bash
# 1. Clone repo
git clone https://github.com/xanh-24/xanh24-landing-pioneer-temp-hdr58orar-xanh-24.git
cd xanh24-landing-pioneer-temp-hdr58orar-xanh-24

# 2. Copy file từ folder xanh24-deploy vào đây
# - index.html -> ghi đè
# - public/video/pioneer-day.mp4 -> tạo folder public/video/ rồi copy

# 3. Push
git add .
git commit -m "V30 final with real video 7.4MB"
git push
```

### Cách 3: Vercel Drag & Drop (nhanh nhất)
1. Vào https://vercel.com/dashboard
2. Chọn project xanh24-landing-pioneer-temp-hdr58orar-xanh-24
3. Vào tab Deployments -> Drag file ZIP xanh24-deploy.zip vào
4. Vercel tự deploy

## Sau deploy test:
- Vào https://...vercel.app/?nocache=1
- Góc phải dưới: popup LIVE TỪ SỰ KIỆN tự play preview
- Bấm vào popup -> modal mở video MB - Xanh24 đón sinh viên Pioneer có tiếng
- Form: Sinh viên / Nhà trường / Đối tác -> nút đổi text
- Submit: Supabase 201
