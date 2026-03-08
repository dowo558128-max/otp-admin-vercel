# لوحة تحكم واتساب OTP — Vercel

لوحة تحكم أمامية فقط (مسح QR / ربط الرقم، حالة الاتصال، إرسال تجريبي) تعمل على Vercel وترتبط بـ API السيرفر الحالي.

## النشر على Vercel

### الطريقة 1: من GitHub

1. انشئ مستودعاً جديداً وارفع محتويات المجلد:
   - `index.html`
   - `config.js`
   - `vercel.json`
2. ادخل إلى [vercel.com](https://vercel.com) واتصل بحساب GitHub.
3. **Add New Project** → اختر المستودع.
4. اضغط **Deploy** (لا حاجة لـ Build Command؛ الموقع ثابت).
5. بعد النشر ستظهر لك رابط مثل: `https://otp-admin-vercel-xxx.vercel.app`

### الطريقة 2: من سطر الأوامر (Vercel CLI)

```bash
cd otp-admin-vercel
npx vercel
```

اتبع التعليمات (تسجيل الدخول إن لزم)، ثم:

```bash
npx vercel --prod
```

لنشر على الإنتاج.

## تغيير عنوان الـ API

عدّل الملف `config.js` وغيَّر قيمة `window.OTP_API_BASE` إلى عنوان السيرفر الذي يشغّل نظام OTP، ثم أعد النشر.

مثال:

```js
window.OTP_API_BASE = 'https://76.13.58.90/otp';
```

## ملاحظات

- **CORS:** السيرفر الحالي مضبوط على `CORS_ORIGIN=*` لذا طلبات من نطاق Vercel تعمل.
- **الواجهة فقط:** الـ Backend (واتساب ويب، إرسال OTP) يبقى على السيرفر `76.13.58.90`؛ Vercel يعرض فقط لوحة التحكم.
