# Xanh24 Smart Campus - Landing FINAL

Bản chốt FINAL 45 - Đã thay logo trong suốt, giữ nguyên hero/header/form.

## Cấu trúc
- index.html: file chính (single-file React, đã embed logo transparent base64 + SEO meta)
- assets/logo-xanh24-transparent.png: logo trong suốt dùng cho header/OG
- assets/logo-xanh24-original.png: bản gốc

## 1. Upload lên GitHub
1. Tạo repo mới: github.com/new -> tên xanh24-smart-campus
2. Trong thư mục này chạy:
```
git init
git add .
git commit -m "feat: Xanh24 Smart Campus FINAL - transparent logo + SEO"
git branch -M main
git remote add origin https://github.com/<username>/xanh24-smart-campus.git
git push -u origin main
```

## 2. Deploy lên Vercel (1 click)
- Vào vercel.com -> Add New Project -> Import Git Repository vừa tạo
- Framework Preset: Other / Static
- Build Command: để trống
- Output Directory: để trống (hoặc .)
- Deploy -> sẽ có domain https://xanh24-smart-campus.vercel.app

Hoặc dùng CLI:
```
npm i -g vercel
vercel --prod
```

File vercel.json đã cấu hình SPA fallback + cache header cho assets.

## 3. Kết nối Supabase (cho form đăng ký Pioneer)

Landing hiện có form. Để lưu data:

a) Tạo project Supabase: supabase.com -> New Project
b) Tạo bảng:
SQL Editor chạy:
```sql
create table pioneer_leads (
  id uuid default gen_random_uuid() primary key,
  full_name text,
  phone text,
  email text,
  school text,
  created_at timestamp default now()
);
-- Bật RLS và cho phép insert public
alter table pioneer_leads enable row level security;
create policy "Allow public insert" on pioneer_leads for insert with check (true);
create policy "Allow read for auth" on pioneer_leads for select using (auth.role() = 'authenticated');
```

c) Lấy URL + anon key ở Project Settings > API
d) Trong index.html, tìm chỗ handleSubmit form (search: handleSubmit / onSubmit) và thay bằng:
```js
const { createClient } = supabase;
const supabaseClient = createClient('YOUR_SUPABASE_URL','YOUR_SUPABASE_ANON_KEY');
await supabaseClient.from('pioneer_leads').insert([{full_name, phone, email, school}]);
```

Nếu bạn muốn mình đấu nối sẵn Supabase vào code, gửi mình URL + anon key mình patch sẵn.

## SEO đã có sẵn
- <title>, description, canonical, OG, Twitter, lang=vi, theme-color #00A651
- Không rebuild hero/form như yêu cầu.

## Logo
- Đã loại bỏ nền trắng, chỉ giữ đồng xu vàng.
- Dùng assets/logo-xanh24-transparent.png cho mọi nơi cần.

Cần hỗ trợ thêm domain xanh24.vn?
- Vercel > Settings > Domains > Add xanh24.vn / smart-campus.xanh24.vn
- Trỏ CNAME về cname.vercel-dns.com


## UPDATE - Supabase Integration (2026-05-13)
- File index.html đã có sẵn script Supabase
- Cần thay ANON_KEY: mở index.html tìm %%ANON_KEY_PLACEHOLDER%% và dán anon key từ Supabase > Settings > API > anon public
- Sau khi dán, push lên GitHub, Vercel tự redeploy
