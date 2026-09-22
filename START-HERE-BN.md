# QX PRO ELITE — সবচেয়ে সহজে APK বানানোর নিয়ম

## শুধু APK বানাতে চাইলে

1. GitHub-এ **New repository** তৈরি করো, যেমন `QXProElite`।
2. এই ZIP-এর **সব ফাইল** repository-তে upload করো। `android` folder upload করার দরকার নেই—এই প্যাকেজে Android project root-এ সাজানো আছে।
3. GitHub → **Actions** → **Build QX PRO ELITE APK** → **Run workflow** চাপো।
4. Build শেষ হলে workflow-এর নিচে **Artifacts** → `QX-PRO-ELITE-APK` → Download করো।
5. ZIP খুলে `app-debug.apk` ফোনে install করো।

## খুব গুরুত্বপূর্ণ

APK build হবে, কিন্তু Login/Market Analysis চালাতে তোমার **HTTPS domain + cPanel PHP/MySQL backend** লাগবে।

Android app-এর এই ফাইলে:

`app/build.gradle.kts`

এই দুইটি value তোমার নিজের domain দিয়ে বদলাবে:

```text
APP_URL = https://YOUR-DOMAIN.com/qxpro/app.php
ALLOWED_HOST = YOUR-DOMAIN.com
```

তারপর GitHub Actions আবার Run করলেই নতুন APK হবে।

## High Protection

- Password APK-এর ভিতরে রাখা নেই
- Server-side password hash
- HTTPS only
- Session regeneration
- Password change করলে পুরোনো sessions invalid
- Screenshot/screen recording blocked
- WebView file access blocked
- Cleartext HTTP blocked
- Release configuration-এ R8 enabled

## Backend

`backend/` folder cPanel-এ HTTPS site-এর `/qxpro/` directory হিসেবে upload করার জন্য।

Database-এর জন্য:

`backend/sql/schema.sql`

ব্যবহার করবে।

প্রথম admin account তৈরি করার পর `setup_admin.php` অবশ্যই server থেকে delete করবে।

> কোনো APK-কে 100% uncrackable বলা যায় না। এই design-এর মূল protection server-side authentication।
