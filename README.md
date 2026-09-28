# UniHub — APK

مستودع لتوزيع ملفات التطبيق المبنية. الكود المصدري في [SagedAMV/app_new](https://github.com/SagedAMV/app_new).

## النسخة الكاملة (المُسلَّمة هذه الجلسة) ⭐

**`UniHub-v1.0.0-release-full.apk`** — نسخة 1.0.0 (versionCode 1)

- نمط البناء: **releaseFull** — جودة Release نفسها (موقّعة بمفتاح الإصدار
  `unihub-release.jks`، توقيع مُتحقَّق منه بـ apksigner، محازة zipalign
  مُتحقَّق منها) **بلا تصغير شيفرة ولا تصغير موارد** (R8 معطّل) — النسخة
  الكاملة فقط، وفق طلب المستخدم.
- الحجم: ~13.3 MB (13,959,321 بايت)
- المتطلبات: Android 8.0+ (minSdk 26) — compileSdk/targetSdk 35
- موقّع بشهادة: CN=UniHub, OU=Personal, O=UniHub, C=SA
- **التنزيل المباشر:** [إصدار v1.0.0-full](https://github.com/SagedAMV/buled/releases/latest)

### التحقق العميق من البناء (الجلسة الثالثة 2026-09-28 — الحالية)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20، Android SDK platform-35 +
  build-tools 35.0.0، Gradle 8.9 عبر الغلاف الرسمي
  `build-release-full.sh`، AGP 8.7.2، Kotlin 2.0.21، KSP 2.0.21-1.0.25 —
  على آلة 2GB/نواتين أُضيف لها Swap ‏2.5GB في بيئة البناء
- **صفر أخطاء بناء هذه الجلسة** — تحقق عميق متعدد الطبقات: مراجعة يدوية
  (AppModule، UniHubApplication، MainActivity، المانيفست وتقاطعها مع
  المصادر، التنقل الآمن الأنواع، قواعد ProGuard/R8 ومحرك هندسة المجرة)
  + بوابات الجودة الثلاث — فلم يلزم أي تعديل شيفرة، ولم يُدفع أي تغيير
  إلى app_new (لا شيء تغيّر)
- مراحل `build-release-full.sh` كلها خضراء:
  - `compileReleaseFullKotlin` ✅ صفر أخطاء وصفر تحذيرات مترجم
  - `testReleaseFullUnitTest` ✅ (بلا مصادر اختبار — حُذفت بعد اكتمال
    تحقق الجلسة السابقة وفق تعليمات.md)
  - `lintVitalReleaseFull` ✅ (التحذيرات الوحيدة داخلية في أداة Lint
    نفسها — عدم توافق Kotlin Analysis API — وليست في شيفرة التطبيق)
  - `assembleReleaseFull` ✅ — **BUILD SUCCESSFUL in 2m 8s**
- العطل البيئي الوحيد: قتّال النظام قتل Daemon غرادل لحظة
  `hiltJavaCompile` (RSS ‏1753MB على آلة بلا Swap — النمط الموثق نفسه في
  جلسات سابقة) — أُصلح بملف Swap ‏2.5GB في بيئة البناء لا في الشيفرة،
  وأُعيد البناء عبر الغلاف فاكتملت المرحلتان خضراوين بخبيئة غرادل
- توقيع مُتحقَّق بـ `apksigner verify` + محاذاة `zipalign -c 4` سليمة
- SHA-256: `a1c4b72b256af08bba161fddb35276b799f30ce8b5e5ab07f21e7c16baea1935`
- المصدر: [SagedAMV/app_new@31f6b99](https://github.com/SagedAMV/app_new/commit/31f6b99)
  (يتضمن تحديثات جلسات المجرة الأخيرة: 42 اختباراً أثبتت حصر الأبناء
  داخل الدائرة الحاضنة وتقوية مصدر الحقيقة الواحد لعرض عمود الابن)

---

### تحقق الجلسة السابقة (2026-09-28 — الثانية، للتأريخ)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20، Android SDK platform-35 +
  build-tools 35.0.0 (+ 34.0.0 جلبه AGP تلقائياً)، Gradle 8.9 عبر الغلاف،
  AGP 8.7.2، Kotlin 2.0.21، KSP 2.0.21-1.0.25 — على آلة 1.9GB مع Swap ‏3GB
- **صفر أخطاء بناء تلك الجلسة** — فلم يلزم أي تعديل شيفرة
- مراحل الغلاف خضراء: compileReleaseFullKotlin ✅، 45 اختبار وحدة ✅،
  lintVital ✅، assembleReleaseFull ✅ في 2m 4s
- توقيع ومحاذاة مُتحقَّق منهما
- SHA-256: `c485428af7290ef797a1464836758fb5501f3148ba73a6a606c31fdea747b367`
- المصدر: [SagedAMV/app_new@264c2ef](https://github.com/SagedAMV/app_new/commit/264c2ef)

---

### تحقق الجلسة السابقة (2026-09-28 — جلسة إصلاح fillMaxWidth، للتأريخ)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20، Android SDK platform-35 +
  build-tools 34.0.0/35.0.0، Gradle 8.9 عبر الغلاف، AGP 8.7.2، Kotlin 2.0.21،
  KSP 2.0.21-1.0.25 — على آلة 1.9GB مع Swap ‏2.5GB
- **وُجد خطأ بناء حقيقي تلك الجلسة وأُصلح من الجذر:** مرجع غير محلول
  `fillMaxWidth` في `GalaxyScreen.kt:603` (استيراد
  `androidx.compose.foundation.layout.fillMaxWidth` ناقص) — كان يكسر
  `compileReleaseFullKotlin` تماماً، ودخل مع تحسينات المجرة في `ce65d68` بعد
  جلسة التحقق السابقة التي لم ترَه. الإصلاح: سطر الاستيراد فقط
  (commit `aa66ee9` في app_new)
- مراحل `build-release-full.sh` كلها خضراء:
  - `compileReleaseFullKotlin` ✅ صفر أخطاء بعد الإصلاح
  - `testReleaseFullUnitTest` ✅ — **45 اختبار وحدة، 0 فشل، 0 خطأ، 0 تخطٍّ**
  - `lintVitalReleaseFull` ✅
  - `assembleReleaseFull` ✅ — اكتمل حتى مع مرحلة دمج الـ dex (ذروة الذاكرة
    داخل حدود الكومة 1024m + Swap)
- توقيع مُتحقَّق بـ `apksigner verify` + محاذاة `zipalign -c 4` سليمة
- SHA-256: `9eb92f4f8b2e045835e7a531dd832d02317d7f774ac8f54af7956fa32d88e4fc`
- المصدر: [SagedAMV/app_new@aa66ee9](https://github.com/SagedAMV/app_new/commit/aa66ee9)

---

### تحقق الجلسة السابقة (2026-09-28 — المستقلة، للتأريخ)

- فحص بناء عميق **مستقل** ببيئة بُنيت من الصفر (OpenJDK 17.0.20، Android SDK
  platform-35 + build-tools 35.0.0، Gradle 8.9 عبر الغلاف) على آلة 1.9GB/نواتين
- **لا أخطاء بناء وُجدت** تلك الجلسة: compileReleaseFullKotlin صفر أخطاء —
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
- ملاحظة: هذه النسخة القديمة حلّت محلّها النسخة الحالية أعلاه (المبنية من
  `aa66ee9` التي تتضمن إصلاحات النسخ الاحتياطي والمجرة + إصلاح البناء)
