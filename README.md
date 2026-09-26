# UniHub — APK

مستودع لتوزيع ملفات التطبيق المبنية. الكود المصدري في [SagedAMV/app_new](https://github.com/SagedAMV/app_new).

## النسخة الكاملة (المُسلَّمة هذه الجلسة) ⭐

**`UniHub-v1.0.0-release-full.apk`** — نسخة 1.0.0 (versionCode 1)

- نمط البناء: **releaseFull** — جودة Release نفسها (موقّعة بمفتاح الإصدار
  `unihub-release.jks`، توقيع v2 مُتحقَّق منه بـ apksigner) **بلا تصغير شيفرة
  ولا تصغير موارد** (R8 معطّل) — النسخة الكاملة كما طلب المستخدم.
- الحجم: ~13.9 MB
- المتطلبات: Android 8.0+ (minSdk 26) — compileSdk/targetSdk 35

### التحقق المرافق للبناء (جلسة التحقق العميق الحالية)

- ترجمة Kotlin + KSP (Room/Hilt): بلا أخطاء
- 36 اختبار وحدة على المتغيّر releaseFull: خضراء كلها (0 إخفاق)
- lintVital: ناجح ضمن مسار assembleReleaseFull
- SHA-256: `d9d282842c4b6b2618abd80bb58acee4855896b2b1ffd9fe58d7a1b5716b60f6`
- المصدر: `SagedAMV/app_new@2c4f53b`

## النسخة المصغّرة (أرشيفية)

**`UniHub-v1.0.0-release-minified.apk`** — Release مع `isMinifyEnabled = true`
و`isShrinkResources = true` (R8 full mode) — ~2.8 MB. قواعد الحماية في
`app/proguard-rules.pro` بمستودع الكود.
