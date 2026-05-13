# GooseRelayWithGithubAction

In this project we are trying to test if we can use **GitHub Actions** as a lightweight Linux VPS to run a **GooseRelayVPN** tunnel.

> Inspired by: [Kianmhz/GooseRelayVPN/issues/120](https://github.com/Kianmhz/GooseRelayVPN/issues/120)

---

## 📖 How to use (راهنمای استفاده)

### 1. Google Script Setup

- یک **اسکریپت جدید** در حساب Google Apps Script خود بسازید.
- محتوای فایل `GoogleScript.gs` را در آن کپی کنید.
- اسکریپت را **Deploy** کنید (فعلاً به ID و URL نیاز نداریم، ولی Google Script را باز نگه دارید – بعداً باید آدرس تونل Bore را در آن اضافه کنید).

### 2. Run GitHub Action

- در مخزن خود، به بخش **Actions** بروید.
- workflow با نام `GooseRelayVPN (manual update)` را انتخاب کنید.
- روی **Run workflow** کلیک کنید تا اجرا شود.
- روی **tunnel** (اکشن در حال اجرا) کلیک کنید تا لاگ‌های ترمینال را ببینید.

### 3. Get Bore Tunnel Address

- در لاگ‌ها، **فلش رو به پایین** کنار `Run GooseRelayVPN server setup (based on user script)` را باز کنید.
- مقدار **Bore tunnel** را کپی کنید (مثال: `http://bore.pub:34778/tunnel`).
- این آدرس را در جای مناسب فایل **GoogleScript.gs** قرار دهید.
- دوباره اسکریپت را **Deploy** کنید.
- **ID دیپلویمنت** را کپی کنید و در فایل `client_config.json` در جای مشخص شده قرار دهید.

### 4. Get Tunnel Key

- به لاگ‌های همان Action برگردید.
- مقدار **Tunnel Key** را کپی کنید (مثال: `797c57415d5a73ae606df4882a362b98817fdd86ecbbb15d0d0e00d2c7dcfbf3`).
- این مقدار را در فایل `client_config.json` در جای مشخص شده قرار دهید.

### 5. Client Configuration

- فایل `client_config.json` را ذخیره کنید.
- آن را در همان پوشه‌ای قرار دهید که فایل `goose-client.exe` (که قبلاً از [GooseRelayVPN](https://github.com/Kianmhz/GooseRelayVPN) گرفته‌اید) وجود دارد.

### 6. Run the Client

- یک ترمینال **CMD** باز کنید.
- فایل `goose-client.exe` را اجرا کنید.

### 7. Use with FoxyProxy (Browser)

- افزونه **FoxyProxy** را روی **Google Chrome** نصب کنید.
- یک پروکسی جدید از نوع **Socks5** با آدرس `127.0.0.1` و پورت `1080` بسازید.
- آن را فعال کنید.
- حالا می‌توانید تست کنید که سایت‌هایی مانند **جمناي، چت جی‌پی‌تی و سایر سایت‌ها** باز می‌شوند یا نه.

---

## ⚠️ Important Notes

- **Bore tunnel ناپایدار است** – تقریباً پس از **20 دقیقه یا کمتر** بسته می‌شود.
- هر بار که تونل بسته شد:
  - Action گیت‌هاب را **Cancel** کنید.
  - دوباره **Run workflow** را بزنید.
  - **آدرس تونل** و **کلید تونل** جدید را کپی کنید.
  - آدرس جدید را در **Google Script** به‌روز کنید، **دوباره Deploy** کنید و **ID جدید** را در `client_config.json` جایگزین کنید.
- **هر بار که آدرس تونل را عوض می‌کنید، باید Google Script را دوباره Deploy کنید** و ID جدید را در فایل JSON وارد کنید.

---

## 🧪 Disclaimer

> **این پروژه صرفاً جنبهٔ آموزشی دارد و به هیچ وجه یک راه‌حل مناسب برای دسترسی به اینترنت نیست.**
