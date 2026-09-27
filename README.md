# UniHub — APK

مستودع لتوزيع ملفات التطبيق المبنية. الكود المصدري في [SagedAMV/app_new](https://github.com/SagedAMV/app_new).

## النسخة الكاملة (المُسلَّمة هذه الجلسة) ⭐

**`UniHub-v1.0.0-release-full.apk`** — نسخة 1.0.0 (versionCode 1)

- نمط البناء: **releaseFull** — جودة Release نفسها (موقّعة بمفتاح الإصدار
  `unihub-release.jks`، توقيع v2 مُتحقَّق منه بـ apksigner، محاذاة zipalign
  مُتحقَّق منها) **بلا تصغير شيفرة ولا تصغير موارد** (R8 معطّل) — النسخة
  الكاملة فقط، وفق طلب المستخدم (أُزيلت النسخة المصغّرة الأرشيفية من هذا
  المستودع لأن الطلب الحالي «النسخة الكاملة فقط»).
- الحجم: ~13.9 MB (13,942,937 بايت)
- المتطلبات: Android 8.0+ (minSdk 26) — compileSdk/targetSdk 35
- موقّع بشهادة: CN=UniHub, OU=Personal, O=UniHub, C=SA

### التحقق العميق المرافق للبناء (جلسة 2026-09-27)

- فحص بناء عميق مستقل: ترجمة Kotlin + KSP (Room/Hilt) على المتغيّر releaseFull
- إصلاح فشل بناء جوهري وُجد أثناء الفحص: نفاد Metaspace
  (AssertionError: Metaspace) أثناء compileReleaseFullKotlin — رُفع سقف
  MaxMetaspaceSize من 320m إلى 512m في gradle.properties (التعديل مرفوع
  لمستودع الكود app_new)
- 36 اختبار وحدة على المتغيّر releaseFull: خضراء كلها (0 إخفاق، 0 خطأ)
- lintVitalReleaseFull: ناجح ضمن مسار البناء
- فحص يدوي: لا دوال خاصة ميتة، لا واردات غير مستعملة فعلياً
- SHA-256: 86189dea3ef7487570b7bd91cea4f009e01a27cc6f68c3b5ed369d69d90c231d
- المصدر: SagedAMV/app_new@4155d06
