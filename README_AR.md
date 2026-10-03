# FMTopo Pro V101

## ما تم تغييره

- حذف إدخال رابط Cloud Run من واجهة الطالب نهائياً.
- الاتصال بخادم Earth Engine أصبح تلقائياً.
- إضافة فحص لحالة الخادم داخل وحدة الاستشعار عن بعد.
- استبدال شعار ZASTopo بشعار FMTopo Pro في الشريط العلوي وصفحة الدخول والملف الشخصي وأيقونة التطبيق.

## طريقة ربط خادم المعالجة دون تدخل الطالب

### الخيار المفضل: نفس نطاق الموقع

انشر واجهة الموقع والخادم خلف النطاق نفسه أو استعمل Firebase Hosting Rewrite. اترك هذا السطر داخل `index.html` كما هو:

```html
<meta name="fmtopo-rs-api" content="">
```

عندها تتصل الواجهة تلقائياً بـ:

```text
/health
/api/v1/remote-sensing/analyze
```

على نطاق الموقع نفسه.

### إذا كان Cloud Run على نطاق منفصل

مدير الموقع فقط يضع الرابط مرة واحدة في رأس `index.html`:

```html
<meta name="fmtopo-rs-api" content="https://YOUR-SERVICE.run.app">
```

لا يظهر هذا الرابط في واجهة الطالب ولا يُطلب منه إدخاله.

## ملفات الشعار

يجب رفع هذه الملفات بجانب `index.html`:

- `fmtopo-logo.webp`
- `fmtopo-icon-192.png`
- `fmtopo-icon-512.png`
- `manifest.webmanifest`

## ملاحظة

الاتصال المباشر بـ Google Earth Engine يحتاج خادماً منشوراً ومهيأً بحساب خدمة ومشروع Earth Engine. لا يمكن تشغيل Earth Engine بأمان من ملف HTML وحده لأن بيانات الاعتماد لا ينبغي وضعها في المتصفح.
