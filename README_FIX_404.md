# V31 CLEAN - Fix 404

## Chỉ cần 2 file này thôi, xóa hết file rác cũ!

Cấu trúc CHUẨN:
```
/
├── index.html              (1.6MB - V30 final)
├── vercel.json             (config Vercel)
└── public/
    └── video/
        ├── pioneer-day.mp4 (7.4MB - video chính)
        └── landing-page-light.mp4 (7.4MB - backup, cùng file)
```

## Cách fix 404 (làm 1 lần):

### Bước 1: Xóa file rác trên GitHub
Vào repo https://github.com/giangcasc-xanh24/xanh24-landing-pioneer-temp
- Xóa hết: INDEX.html, index_1.html, Landing_Page_1_light.mp4 (root), Admin.html, README_*.md
- Chỉ giữ lại: index.html (sẽ up lại) và folder public/video/

Cách xóa: Vào file -> Bấm nút thùng rác (Delete) -> Commit

### Bước 2: Up bộ CLEAN này
Giải nén xanh24-clean-v31.zip -> sẽ có folder xanh24-clean-v31
Kéo 3 file/thư mục vào GitHub:
- index.html -> kéo vào root
- vercel.json -> kéo vào root  
- public/ -> kéo vào root (chọn Upload folder)

Hoặc dùng Git:
```
git clone <repo-url>
rm -rf INDEX.html index_*.html Landing_Page* Admin.html README_*.md
cp -r ~/Downloads/xanh24-clean-v31/* .
git add .
git commit -m "V31 CLEAN fix 404 - only index.html + public/video/"
git push
```

### Bước 3: Vercel sẽ tự deploy lại, hết 404
Vào Vercel Dashboard -> Deployments -> Xem Latest -> Ready
