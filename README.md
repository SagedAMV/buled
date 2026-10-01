# توزيع ملفات APK

مستودع لتوزيع ملفات التطبيقات المبنية.

## تطبيقي (Tatbiqi) v3.1.2 — النسخة الكاملة (المُسلَّمة هذه الجلسة) ⭐

**`Tatbiqi-v3.1.2-release-full.apk`** — نسخة 3.1.2 (versionCode 14) من تطبيق
«تطبيقي» — الكود المصدري في [SagedAMV/app_doll_kotlin](https://github.com/SagedAMV/app_doll_kotlin)

- نمط البناء: **release** الرسمي للمشروع — نسخة الإصدار الكاملة، موقّعة
  بمفتاح إصدار جديد (صلاحية 10000 يوم)، التوقيع مُتحقَّق منه بـ apksigner
- الحجم: ~4.2 MB (4,375,943 بايت)
- المتطلبات: Android 8.0+ (minSdk 26) — compileSdk/targetSdk 34
- موقّع بشهادة: CN=Tatbiqi, OU=Personal, O=Tatbiqi, C=SA
- SHA-256: `892eb9c22b665c085335667bc364cce4607ef33371f10a31fd251a34dcd6e484`
- **التنزيل المباشر:** [إصدار tatbiqi-v3.1.2](https://github.com/SagedAMV/buled/releases/latest)

### التحقق العميق من البناء وإصلاحاته (جلسة 2026-09-29)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20.1، Android SDK platform-34 +
  build-tools 34.0.0، Gradle 8.9 عبر الغلاف، AGP 8.6.1، Kotlin 2.0.20،
  KSP 2.0.20-1.0.25، Hilt 2.52 — نجح `assembleDebug` و `assembleRelease`
  كاملاً بلا أي خطأ في شيفرة التطبيق (صفر أخطاء ترجمة في 67 ملف Kotlin)
- **أخطاء البناء التي رُصدت وأُصلحت (مرفوعة لمستودع
  [app_doll_kotlin](https://github.com/SagedAMV/app_doll_kotlin) — commit
  `90d2553`):**
  - 🔴 `google-services.json` كان في جذر المشروع بينما `google-services
    plugin` يقرؤه حصراً من `app/` — نُقل إلى موقعه الصحيح وأُزيلت قاعدة
    تجاهله من `.gitignore` حتى يبقى متتبعاً
  - 🔴 لا يوجد إعداد توقيع لنسخة الإصدار إطلاقاً (الناتج كان يبقى غير
    قابل للتثبيت) — أُنشئ `release.keystore` + `keystore.properties`
    ورُبط `signingConfig` بـ buildType release
  - 🟡 كومة Gradle ‏700m كانت دون حاجة ترجمة Compose+KSP+R8 — رُفعت إلى
    1536m مع MaxMetaspace ‏512m في `gradle.properties`
- الفحص: `apksigner verify --print-certs` ناجح على الناتج النهائي

---

## UniHub v1.3.1 — النسخة الكاملة (المُسلَّمة هذه الجلسة) ⭐

**`UniHub-v1.3.1-release-full.apk`** — نسخة 1.3.1 (versionCode 5) — الكود
المصدري في [SagedAMV/app_new](https://github.com/SagedAMV/app_new)

- نمط البناء: **releaseFull** — جودة Release نفسها (موقّعة بمفتاح الإصدار
  `unihub-release.jks`، توقيع مُتحقَّق منه بـ apksigner، محازاة zipalign
  مُتحقَّق منها) **بلا تصغير شيفرة ولا تصغير موارد** (R8 معطّل) — النسخة
  الكاملة فقط، وفق طلب المستخدم.
- الحجم: ~13.5 MB (14,172,345 بايت)
- المتطلبات: Android 8.0+ (minSdk 26) — compileSdk/targetSdk 35
- موقّع بشهادة: CN=UniHub, OU=Personal, O=UniHub, C=SA (بصمة SHA-256
  `5109c404c5cd4d207d0ee0dc1f1ed77b58fd0269b28d8fc2520aaff1a36b74ca` —
  مفتاح المستودع نفسه، تحديث فوق التثبيت للتسليمات السابقة)
- SHA-256: `66e5697ef1b23e32e9a68ed14025b275d2ebde4ad6ebc6c2d858a25820e79966`

### التحقق العميق من البناء وإصلاحاته (جلسة 2026-10-01)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20، Android SDK platform-35 +
  build-tools 34.0.0، Gradle 8.9 عبر الغلاف، AGP 8.7.2، Kotlin 2.0.21،
  KSP 2.0.21-1.0.25 — على آلة 2GB بلا Swap؛ ضبط الذاكرة الموثق في
  gradle.properties (كومة 832m + SerialGC + in-process) عمل كما صُمم ولم
  ينقطع البناء في أي مرحلة.
- **خطأ البناء الذي رُصد وأُصلح (مرفوع لمستودع
  [app_new](https://github.com/SagedAMV/app_new) — commit `1e2322f`):**
  - 🔴 4 اختبارات فاشلة في `DestinationFolderTreeTest` (شجرة وجهة التنزيل)
    — الجذر في `DestinationFolderTree.kt`: المسح التكميلي كان يرقّي أبناء
    المجلدات المطوية إلى المستوى الأعلى، و`childrenOf` كان يعيد الفرز
    فيمسح ترتيب المصدر. الإصلاح: ترشيح مستقر + مسح يرقّي غير القابل
    للبلوغ فقط (أب مفقود أو دورة parentId) — الاختبارات الثمانية خضراء
    دون تعديل عليها.
  - 🟡 `gradlew` وغلاف البناء بلا بت تنفيذ (Permission denied عند أي استنساخ
    جديد) — أُعيد بت التنفيذ لهما.
- البوابات الأربع خضراء: compile (3m33s) → tests (125 اختباراً، صفر فشل،
  3 متخطاة = اختبارات R2 الحية المعطلة افتراضياً) → lintVital →
  assemble (2m26s). فحص يدوي: صفر force-unwrap، صفر TODO/FIXME، صفر
  تحذيرات مترجم. التفاصيل في `verification/deep-check-2026/` بمستودع
  app_new.

---

## UniHub — النسخة الكاملة (جلسة سابقة)

**`UniHub-v1.2.0-release-full.apk`** — نسخة 1.2.0 (versionCode 3)

- نمط البناء: **releaseFull** — جودة Release نفسها (موقّعة بمفتاح الإصدار
  `unihub-release.jks`، توقيع مُتحقَّق منه بـ apksigner، محازة zipalign
  مُتحقَّق منها) **بلا تصغير شيفرة ولا تصغير موارد** (R8 معطّل) — النسخة
  الكاملة فقط، وفق طلب المستخدم.
- الحجم: ~13.3 MB (13,959,321 بايت)
- المتطلبات: Android 8.0+ (minSdk 26) — compileSdk/targetSdk 35
- موقّع بشهادة: CN=UniHub, OU=Personal, O=UniHub, C=SA
- **التنزيل المباشر:** [إصدار v1.2.0-full](https://github.com/SagedAMV/buled/releases/latest)

### التحقق العميق من البناء (الجلسة السابعة 2026-09-29 — الحالية)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20.1، Android SDK platform-35 +
  build-tools 35.0.0، Gradle 8.9 عبر الغلاف، AGP 8.7.2، Kotlin 2.0.21،
  KSP 2.0.21-1.0.25 — على آلة 1.99GB/نواتين **بلا Swap**؛ عند بلوغ ذروة
  `mergeDexReleaseFull` في المحاولة الأولى قتل قتّال النظام الدايمون
  («Gradle build daemon disappeared unexpectedly» الموثّقة في
  gradle.properties) — وأُصلح هذه المرة **من الجذر في الإعدادات لا بملف
  Swap**: خُفضت كومة Daemon غرادل من 1024m إلى 832m (ذروة الترجمة الفعلية
  دون 700m كما وثّقت الجلسات السابقة، فالخفض آمن) مع توثيق التشخيص كاملاً
  في `gradle.properties` (commit `a114b80` في app_new)، فاكتمل البناء
  بعدها مستقراً بلا Swap إطلاقاً
- **صفر أخطاء بناء في شيفرة التطبيق** — تحقق عميق: بوابات الجودة
  (compile/test/lintVital) + فحص يدوي شامل: صفر دوال ميتة (مسح آلي لكل
  دوال public/internal/private)، صفر TODO/FIXME، صفر force-unwrap (`!!`)،
  ومراجعة يدوية للملفات المركزية (UniHubApplication، AppModule،
  MainActivity، محرك تخطيط المجرة، المانيفست) — فلم يلزم أي تعديل في
  شيفرة التطبيق نفسها
- **التعديلات (مرفوعة لمستودع app_new):**
  - رفع رقم الإصدار إلى 1.2.0 (versionCode 3) وفق طلب المستخدم
    (commit `998ca7c`)
  - إصلاح انقطاع البناء الموثّق أعلاه: كومة Daemon ‏1024m → 832m في
    `gradle.properties` (commit `a114b80`)
- مراحل الغلاف كلها خضراء:
  - `compileReleaseFullKotlin` ✅ صفر أخطاء
  - `testReleaseFullUnitTest` ✅ (بلا مصادر اختبار — حُذفت بعد اكتمال
    تحقق الجلسات السابقة وفق تعليمات.md)
  - `lintVitalReleaseFull` ✅
  - `assembleReleaseFull` ✅ — BUILD SUCCESSFUL in 33s + محاذاة
    `zipalign -c 4` ✅ + توقيع `apksigner verify` ✅ (مخطط v2، موقّع واحد)
- SHA-256: `62e949d88b36e9beb5255f6563a193e2348c443be9ea7f810f886c0c2107ce60`
- المصدر: [SagedAMV/app_new@a114b80](https://github.com/SagedAMV/app_new/commit/a114b80)
  (رأس main الحالي — يتضمن رفع الإصدار وإصلاح كومة Daemon لهذه الجلسة
  وكل جلسات المجرة والنسخ الاحتياطي السابقة)

---

### تحقق الجلسة السابقة (2026-09-29 — السادسة، للتأريخ)

- سلّمت النسخة الكاملة **UniHub v1.1.0** (versionCode 2) باسم
  `UniHub-v1.1.0-release-full.apk`
- بيئة بُنيت من الصفر: OpenJDK 17.0.20.1، Android SDK platform-35 +
  build-tools 34.0.0، Gradle 8.9 عبر الغلاف، AGP 8.7.2، Kotlin 2.0.21،
  KSP 2.0.21-1.0.25 — على آلة 2GB/نواتين؛ عند بلوغ ذروة
  `mergeExtDexReleaseFull` في المحاولة الأولى قتل قتّال النظام الدايمون
  («Gradle build daemon disappeared unexpectedly» الموثّقة في
  gradle.properties) فأُصلح من الجذر بملف Swap ‏2GB في بيئة البناء (لا في
  الشيفرة — نهج الجلسة المستقلة نفسه)، واكتمل البناء بعدها مستقراً
- **صفر أخطاء بناء في شيفرة التطبيق** — تحقق عميق: بوابات الجودة
  (compile/test/lintVital/assemble) + مسح `lintReleaseFull` الشامل:
  صفر خطأ، و46 تحذيراً غير حاسم كلها إشعارات (إصدارات أحدث للمكتبات
  GradleDependency×40، وAutoboxingStateCreation×7،
  وObsoleteLintCustomCheck×3، وAndroidGradlePluginVersion×2،
  وObsoleteSdkInt×1) — بلا أثر على البناء أو السلوك، فلم تُمَس شيفرة
  التطبيق
- **التعديل الوحيد:** رفع رقم الإصدار إلى 1.1.0 (versionCode 2) وفق طلب
  المستخدم (commit `b3758a5` في app_new، مرفوع للمستودع)
- مراحل الغلاف كلها خضراء:
  - `compileReleaseFullKotlin` ✅ صفر أخطاء (BUILD SUCCESSFUL in 5m 39s)
  - `testReleaseFullUnitTest` ✅ (بلا مصادر اختبار — حُذفت بعد اكتمال
    تحقق الجلسات السابقة وفق تعليمات.md)
  - `lintVitalReleaseFull` ✅ + `lintReleaseFull` الشامل ✅ صفر خطأ
  - `assembleReleaseFull` ✅ — BUILD SUCCESSFUL in 55s + محاذاة
    `zipalign -c 4` ✅ + توقيع `apksigner verify` ✅
- SHA-256: `ea5ea648c1259f20772f33bcb0d449273ed5a2a027c063a50794b0153081f063`
- المصدر: [SagedAMV/app_new@b3758a5](https://github.com/SagedAMV/app_new/commit/b3758a560dab593ab472e4058301893f785d4031)

---

### تحقق الجلسة السابقة (2026-09-28 — الخامسة، للتأريخ)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20.1، Android SDK platform-35 +
  build-tools 34.0.0، Gradle 8.9 عبر الغلاف الرسمي
  `build-release-full.sh`، AGP 8.7.2، Kotlin 2.0.21، KSP 2.0.21-1.0.25
  — على آلة 2GB/نواتين مع ملف Swap ‏3GB كاحتياط
- **صفر أخطاء بناء في شيفرة التطبيق** — تحقق عميق متعدد الطبقات: مراجعة
  يدوية (هندسة المجرّة ومحرك تخطيطها وشاشتها ونموذجها، AppModule،
  UniHubApplication، MainActivity، المانيفست، التنقل الآمن الأنواع، قواعد
  ProGuard/R8) + فحص دوال ميتة آلي شامل لكل ملفات الشيفرة (public و
  internal وprivate) بصفر نتائج + بوابات الجودة الأربع
- **وُجد خلل توثيقي واحد وأُصلح من الجذر** (بلا أثر سلوكي): تعليق
  WorkManager في `UniHubApplication.kt` كان ينسب اكتشاف واجهة
  `Configuration.Provider` للمهيّئ الافتراضي، بينما المهيّئ الافتراضي
  مُزال من المانيفست (`tools:node="remove"`) والتهيئة فعلياً عند الطلب —
  صُحِّح التعليق ليطابق الآلية الحقيقية المعتمدة (commit `85caba5` في
  app_new، مرفوع للمستودع)
- مراحل الغلاف كلها خضراء (نُفذت السلسلة مرتين: على الشيفرة الأصلية ثم بعد
  التصحيح — والأرقام أدناه لبناء النسخة المُسلَّمة):
  - `compileReleaseFullKotlin` ✅ صفر أخطاء
  - `testReleaseFullUnitTest` ✅ (بلا مصادر اختبار — حُذفت بعد اكتمال
    تحقق الجلسات السابقة وفق تعليمات.md)
  - `lintVitalReleaseFull` ✅ (التحذيرات الوحيدة داخلية في أداة Lint
    نفسها وليست في شيفرة التطبيق)
  - `assembleReleaseFull` ✅ + محاذاة `zipalign -c 4` ✅ + توقيع
    `apksigner verify` ✅
- SHA-256: `c7bec37d6bceb1c0e8d4f3aedbb6ad3342865ed79834732819ade67423bcebba`
- المصدر: [SagedAMV/app_new@85caba5](https://github.com/SagedAMV/app_new/commit/85caba5b06b72c15e15230fe1220ef49f9910eeb)
  (رأس main الحالي)

---

### تحقق الجلسة السابقة (2026-09-28 — الرابعة، للتأريخ)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20.1، Android SDK platform-35 +
  build-tools 34.0.0، Gradle 8.9 عبر الغلاف الرسمي
  `build-release-full.sh`، AGP 8.7.2، Kotlin 2.0.21، KSP 2.0.21-1.0.25 —
  على آلة 2GB/نواتين **بلا Swap**
- **صفر أخطاء بناء في شيفرة التطبيق** — تحقق عميق متعدد الطبقات: مراجعة
  يدوية (محرك تخطيط المجرة وهندستها وشاشتها، AppModule،
  UniHubApplication، MainActivity، المانيفست، التنقل الآمن الأنواع،
  UniHubDatabase، مستودع النسخ الاحتياطي ومسار المشاركة، قواعد
  ProGuard/R8) + بوابات الجودة الثلاث — فلم يلزم أي تعديل شيفرة تطبيق
- **وُجد خطأ بناء واحد في غلاف البناء نفسه وأُصلح من الجذر:** استدعاء
  المرحلة الأولى الموحّد (`compileReleaseFullKotlin testReleaseFullUnitTest
  lintVitalReleaseFull` في عملية غرادل واحدة) قتل قتّال النظام دايمونه
  بصمت («Gradle build daemon disappeared unexpectedly») بعد اكتمال
  الترجمة — أصناف مترجم كوتلن/KSP تبقى محتجزة في Metaspace (~512m) فوق
  الكومة، فإذا دخل lintVital في العملية نفسها تجاوز RSS الإجمالي ذاكرة
  الآلة (2GB بلا Swap). الإصلاح في `build-release-full.sh`
  (commit `2b4d042` في app_new، مرفوع للمستودع): فصل البوابات الثلاث إلى
  عمليات غرادل متعاقبة بذاكرة نظيفة لكل بوابة — فصار البناء مستقراً
- مراحل الغلاف المُحدَّث كلها خضراء:
  - `compileReleaseFullKotlin` ✅ صفر أخطاء وصفر تحذيرات مترجم
  - `testReleaseFullUnitTest` ✅ (بلا مصادر اختبار — حُذفت بعد اكتمال
    تحقق الجلسات السابقة وفق تعليمات.md)
  - `lintVitalReleaseFull` ✅ (التحذيرات الوحيدة داخلية في أداة Lint
    نفسها — عدم توافق Kotlin Analysis API — وليست في شيفرة التطبيق)
  - `assembleReleaseFull` ✅ — **BUILD SUCCESSFUL in 2m 6s** (اكتمل دمج
    الـ dex رغم بلوغ الذروة ~1.7GB لأن الدايمون عملية نظيفة بلا أصناف
    المترجم)
- توقيع مُتحقَّق بـ `apksigner verify` + محاذاة `zipalign -c 4` سليمة
- SHA-256: `90e1e9ba0a2e27ddb59f8ce2c7efbd48632a3955fc1f4f693efea4ef5c0d3b13`
- المصدر: [SagedAMV/app_new@2b4d042](https://github.com/SagedAMV/app_new/commit/2b4d042)
  (رأس main الحالي — يتضمن تحصين غلاف البناء لهذه الجلسة وكل تحديثات
  جلسات المجرة والنسخ الاحتياطي السابقة)

---

### تحقق الجلسة السابقة (2026-09-28 — الثالثة، للتأريخ)

- بيئة بُنيت من الصفر: OpenJDK 17.0.20، Android SDK platform-35 +
  build-tools 35.0.0، Gradle 8.9 عبر الغلاف الرسمي، AGP 8.7.2، Kotlin
  2.0.21 — على آلة 2GB/نواتين أُضيف لها Swap ‏2.5GB في بيئة البناء
- صفر أخطاء بناء — مراجعة يدوية + بوابات الجودة الثلاث، فلم يلزم أي
  تعديل شيفرة
- المراحل كلها خضراء: compile ✅ صفر أخطاء وتحذيرات، test ✅، lintVital
  ✅، assemble ✅ في 2m 8s — توقيع ومحاذاة مُتحقَّق منهما
- SHA-256: `a1c4b72b256af08bba161fddb35276b799f30ce8b5e5ab07f21e7c16baea1935`
- المصدر: [SagedAMV/app_new@31f6b99](https://github.com/SagedAMV/app_new/commit/31f6b99)

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
