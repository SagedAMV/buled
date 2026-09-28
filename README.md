# UniHub — APK

مستودع لتوزيع ملفات التطبيق المبنية. الكود المصدري في [SagedAMV/app_new](https://github.com/SagedAMV/app_new).

## النسخة الكاملة (المُسلَّمة هذه الجلسة) ⭐

**`UniHub-v1.0.0-release-full.apk`** — نسخة 1.0.0 (versionCode 1)

- نمط البناء: **releaseFull** — جودة Release نفسها (موقّعة بمفتاح الإصدار
  `unihub-release.jks`، توقيع مُتحقَّق منه بـ apksigner، محاذاة zipalign
  مُتحقَّق منها) **بلا تصغير شيفرة ولا تصغير موارد** (R8 معطّل) — النسخة
  الكاملة فقط، وفق طلب المستخدم.
- الحجم: ~13.6 MB (13,942,937 بايت)
- المتطلبات: Android 8.0+ (minSdk 26) — compileSdk/targetSdk 35
- موقّع بشهادة: CN=UniHub, OU=Personal, O=UniHub, C=SA
- **التنزيل المباشر:** [إصدار v1.0.0-full](https://github.com/SagedAMV/buled/releases/latest)

### التحقق العميق المرافق للبناء (جلسة 2026-09-28 — المستقلة)

- فحص بناء عميق **مستقل** ببيئة بُنيت من الصفر (OpenJDK 17.0.20، Android SDK
  platform-35 + build-tools 35.0.0، Gradle 8.9 عبر الغلاف) على آلة 1.9GB/نواتين
- **لا أخطاء بناء وُجدت** هذه الجلسة أيضاً: compileReleaseFullKotlin صفر أخطاء —
  فلم يلزم أي تعديل شيفرة (التقرير الكامل في app_new:
  تقرير_جلسة_التحقق_العميق_المستقل_2026-09-28.md)
- 39 اختبار وحدة على المتغيّر releaseFull: خضراء كلها (0 إخفاق، 0 خطأ، 0 تخطٍّ)
- lintVitalReleaseFull: ناجح ضمن مسار البناء
- فحص دوال ميتة (private/internal غير مُشار إليها): صفر نتيجة
- مراجعة يدوية: AndroidManifest، AppModule، UniHubApplication، MainActivity — سليمة
- العطل الوحيد المُشخَّص: قتّال النظام قتل Daemon غرادل لحظة hiltJavaCompile
  (RSS 1698MB على آلة بلا Swap) — أُصلح من الجذر بملف Swap 3GB في بيئة البناء،
  لا في الشيفرة؛ ذروة Swap في مرحلة الدمج 176MB فقط
- توقيع مُتحقَّق بـ apksigner + محاذاة zipalign مُتحقَّق منها
- SHA-256: 2887d11e4c2849647816e2a4829db5f879265d7ebbc5adacec0b1a5dc8736cae
- المصدر: SagedAMV/app_new@e5cc1e2
