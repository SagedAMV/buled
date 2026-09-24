# UniHub — نسخة Release المصغّرة (APK)

مستودع لتوزيع ملف التطبيق المصغّر فقط. الكود المصدري في [SagedAMV/app_new](https://github.com/SagedAMV/app_new).

## الملف

**`UniHub-v1.0.0-release-minified.apk`** — نسخة 1.0.0 (versionCode 1)

- نمط البناء: **Release** مع `isMinifyEnabled = true` و`isShrinkResources = true` (R8 full mode)
- موقّعة بمفتاح المشروع (`unihub-release.jks`) — توقيع v2 مُتحقَّق منه بـ apksigner
- الحجم: ~2.8 MB بعد التصغير وتقليص الموارد
- المتطلبات: Android 8.0+ (minSdk 26)

## التحقق المرافق للبناء

- ترجمة Kotlin + KSP (Room/Hilt): بلا أخطاء
- 25 اختبار وحدة: خضراء كلها
- قواعد R8 الواقية (مُنشئات RoomDatabase وWorkManager وkotlinx.serialization) من
  `app/proguard-rules.pro` في مستودع الكود
