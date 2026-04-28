# Lumixy

`Lumixy` هو مشروع دليل خدمات محلي مبني كتطبيق `Expo / React Native` مع باكند `Laravel API`. يوفّر تجربة تصفح عامة لمزودي الخدمات المعتمدين، مع مسارات منفصلة لمزود الخدمة والإدارة.

## نظرة عامة

يتكوّن المشروع من جزأين رئيسيين:

- تطبيق الموبايل في جذر المستودع.
- الباكند داخل مجلد `Lumixy-backend`.

التطبيق العام يركّز حالياً على:

- استعراض مزودي الخدمات المعتمدين.
- البحث حسب التصنيف.
- الفلترة حسب المدينة.
- عرض صفحة تفاصيل كل مزود.
- إظهار بيانات احتياطية `fallback` عند تعذّر الوصول إلى الـ API أثناء التطوير.

أما الباكند فيوفّر:

- تسجيل مزود خدمة.
- تسجيل الدخول لمزود الخدمة والإدارة.
- إدارة الملف الشخصي والخدمات والموقع وساعات العمل.
- رفع صور الملف الشخصي والمعرض.
- إرسال طلب اعتماد.
- مراجعة الطلبات من الإدارة.
- استعادة كلمة المرور عبر OTP على البريد الإلكتروني.

## التقنيات المستخدمة

### الواجهة الأمامية
- Expo 54
- React Native 0.81
- Expo Router
- TypeScript
- TanStack Query
- Axios
- React Hook Form

### الباكند
- Laravel 12
- PHP 8.2+
- Laravel Sanctum
- Vite
- قاعدة بيانات relational مثل MySQL أو SQLite

## هيكل المشروع

```text
Lumixy/
├─ app/                   مسارات وشاشات Expo Router
├─ components/            مكونات الواجهة
├─ services/              الاتصال مع الـ API وتجهيز البيانات
├─ theme/                 الألوان والخطوط والهوية البصرية
├─ assets/                الصور والأيقونات
├─ constants/             ثوابت عامة
├─ hooks/                 هوكات مخصصة
├─ scripts/               سكربتات مساعدة
├─ package.json           إعدادات تطبيق Expo
└─ Lumixy-backend/        مشروع Laravel API
```

## الميزات الحالية

### التطبيق العام
- شاشة دخول افتتاحية ومسار اختيار بين التصفح أو مسار مزود الخدمة.
- الصفحة الرئيسية تعرض:
  - رسائل تعريفية متغيرة.
  - التصنيفات المتاحة.
  - المزودين الظاهرين حالياً.
- شاشة البحث تدعم:
  - البحث النصي.
  - الفلترة حسب التصنيف.
  - الفلترة حسب مدن الضفة الغربية.
- شاشة تفاصيل المزود تعرض:
  - الصورة الشخصية.
  - التصنيف.
  - النبذة.
  - الخدمات.
  - وسائل التواصل.
  - ساعات العمل.
  - المعرض.

### الباكند
- مسارات عامة للتصنيفات والمزودين.
- Pagination للمزودين في المسارات العامة.
- إدارة ملفات مزودي الخدمة.
- رفع صور الملف الشخصي والمعرض.
- اعتماد / رفض / إيقاف المزود من لوحة الإدارة عبر الـ API.
- استرجاع كلمة المرور عبر OTP.
- Seeder للتصنيفات والمدن من ملفات JSON.
- صفحة اختبار يدوية داخل:
  - `Lumixy-backend/public/tester.html`

## حالة المشروع

- الواجهة العامة مربوطة فعلياً مع الـ API.
- عند فشل الاتصال بالباكند، التطبيق يعرض بيانات احتياطية داخلية لتسهيل التطوير.
- بعض شاشات `provider/admin` في تطبيق الموبايل ما زالت أولية من ناحية الواجهة أو الربط الكامل، بينما الـ API الخاص بها موجود في الباكند.

## التشغيل المحلي

## المتطلبات

- Node.js 18+
- npm
- PHP 8.2+
- Composer
- MySQL أو SQLite

## تشغيل الباكند

```bash
cd Lumixy-backend
composer install
npm install
```

أنشئ ملف `.env` داخل `Lumixy-backend` وأضف القيم المناسبة، ثم نفّذ:

```bash
php artisan key:generate
php artisan migrate --seed
php artisan storage:link
php artisan serve
```

سيعمل الباكند افتراضياً على:

```text
http://127.0.0.1:8000
```

والـ API على:

```text
http://127.0.0.1:8000/api
```

## مثال `.env` للباكند

```env
APP_NAME=Lumixy
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://127.0.0.1:8000

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=lumixy
DB_USERNAME=root
DB_PASSWORD=

FILESYSTEM_DISK=public

MAIL_MAILER=smtp
MAIL_HOST=127.0.0.1
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_FROM_ADDRESS=no-reply@lumixy.local
MAIL_FROM_NAME="Lumixy"
```

## تشغيل تطبيق Expo

من جذر المشروع:

```bash
npm install
npm run start
```

أو:

```bash
npm run android
npm run ios
npm run web
```

## مثال `.env` للتطبيق

في جذر المشروع:

```env
EXPO_PUBLIC_API_URL=http://127.0.0.1:8000/api
```

## ملاحظات الاتصال بين التطبيق والباكند

إذا لم يتم تعريف `EXPO_PUBLIC_API_URL`، فالتطبيق يحاول تحديد عنوان الخادم تلقائياً كالتالي:

- استخدام عنوان الخادم المحدد يدوياً إذا كان موجوداً.
- محاولة استنتاج عنوان Laravel من جلسة Expo المحلية.
- استخدام `10.0.2.2:8000/api` على محاكي Android.
- استخدام `127.0.0.1:8000/api` على iOS أو Web.

## أوامر مفيدة

### الواجهة الأمامية
```bash
npm run start
npm run android
npm run ios
npm run web
npm run lint
```

### الباكند
```bash
cd Lumixy-backend
composer run dev
php artisan test
```

## أهم المسارات البرمجية

### في تطبيق Expo
- `app/(tabs)/index.tsx` الصفحة الرئيسية العامة
- `app/(tabs)/search.tsx` البحث والفلترة
- `app/providers/[id].tsx` صفحة تفاصيل المزود
- `services/api/client.ts` إعداد الاتصال مع الـ API
- `services/public-directory.ts` تجهيز بيانات الدليل العام

### في Laravel
- `routes/api.php` تعريف جميع مسارات الـ API
- `app/Http/Controllers/Api/PublicProviderController.php` المسارات العامة
- `app/Http/Controllers/Api/ProviderAuthController.php` تسجيل ودخول مزود الخدمة
- `app/Http/Controllers/Api/ProviderProfileController.php` إدارة الملف الشخصي
- `app/Http/Controllers/Api/ProviderGalleryController.php` إدارة المعرض
- `app/Http/Controllers/Api/ProviderSubmissionController.php` إرسال الطلب ومتابعة حالته
- `app/Http/Controllers/Api/AdminProviderController.php` مراجعة المزودين من الإدارة
- `app/Http/Controllers/Api/PasswordResetController.php` OTP وإعادة تعيين كلمة المرور

## ملخص الـ API

### Public
- `GET /api/service-categories`
- `GET /api/providers`
- `GET /api/providers/featured`
- `GET /api/providers/{id}`

### Auth
- `POST /api/auth/login`
- `POST /api/admin/auth/login`
- `POST /api/auth/forgot-password`
- `POST /api/auth/verify-otp`
- `POST /api/auth/reset-password`

### Provider
- `POST /api/provider/auth/register`
- `GET /api/provider/me`
- `GET /api/provider/profile`
- `PUT /api/provider/profile/basic`
- `PUT /api/provider/profile/business`
- `POST /api/provider/profile/image`
- `PUT /api/provider/profile/location`
- `PUT /api/provider/profile/contact`
- `PUT /api/provider/profile/working-hours`
- `PUT /api/provider/profile/location-schedule`
- `GET /api/provider/gallery`
- `POST /api/provider/gallery`
- `DELETE /api/provider/gallery/{id}`
- `POST /api/provider/submit`
- `GET /api/provider/application-status`

### Admin
- `GET /api/admin/me`
- `GET /api/admin/admins`
- `POST /api/admin/admins`
- `DELETE /api/admin/admins/{id}`
- `GET /api/admin/categories`
- `POST /api/admin/categories`
- `PUT /api/admin/categories/{id}`
- `DELETE /api/admin/categories/{id}`
- `GET /api/admin/providers/pending`
- `GET /api/admin/providers`
- `GET /api/admin/providers/{id}`
- `POST /api/admin/providers/{id}/approve`
- `POST /api/admin/providers/{id}/reject`
- `POST /api/admin/providers/{id}/suspend`
- `DELETE /api/admin/providers/{id}`

## البيانات الأولية

يستخدم الباكند ملفات JSON جاهزة لتوليد البيانات الأساسية:

- `Lumixy-backend/database/data/service_categories.json`
- `Lumixy-backend/database/data/cities.json`

ويتم تحميلها عبر:

- `ServiceCategorySeeder`
- `CitySeeder`

## الاختبارات

حالياً يوجد اختبار Feature في الباكند يغطي جزءاً من تدفق استعادة كلمة المرور عبر OTP، ويمكن تشغيل الاختبارات عبر:

```bash
cd Lumixy-backend
php artisan test
```

## ملاحظات إضافية

- المشروع مناسب كتطبيق موبايل مع API منفصل.
- البنية الحالية تسمح بتطوير لوحة مزود الخدمة ولوحة الإدارة بشكل تدريجي فوق الـ API الموجود.
- يمكن تشغيل الواجهة العامة حتى عند غياب الخادم بفضل بيانات `fallback` المدمجة في التطبيق.
``` ````
