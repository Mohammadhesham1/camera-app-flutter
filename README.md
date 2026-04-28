# 📸 تطبيق الكاميرا

تطبيق Flutter كاميرا بسيط وأنيق، مع GitHub Actions يبني APK تلقائياً.

---

## ✨ الفيتشرز

- 📷 تصوير عالي الجودة
- 🔦 فلاش / تورش
- 🔄 تبديل بين الكاميرا الأمامية والخلفية
- 🖼️ جاليري للصور المسبقة
- 🔍 عرض الصورة كاملة مع zoom

---

## 🚀 إزاي تشغّله محلياً

```bash
# 1. نزّل الـ dependencies
flutter pub get

# 2. شغّل على جهاز/محاكي
flutter run

# 3. أو ابني APK
flutter build apk --release --split-per-abi
```

---

## ⚙️ إعداد GitHub Actions

### الـ workflow بيشتغل إزاي؟

| الحدث | اللي بيحصل |
|-------|------------|
| `push` على main | بيبني APK ويرفعه كـ artifact |
| `git tag v1.0.0` | بيبني APK **وبيعمل GitHub Release** |

### خطوات رفع المشروع:

```bash
# 1. ابعت المشروع لـ GitHub
git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin main

# GitHub Actions هيشتغل تلقائياً ✅

# 2. عشان تعمل Release رسمي:
git tag v1.0.0
git push origin v1.0.0
# هيعمل Release فيه الـ APK تلقائياً 🚀
```

### فين الـ APK بعد البناء؟

- **Artifacts**: اضغط على الـ workflow run → Artifacts → حمّل الـ zip
- **Releases**: `github.com/USERNAME/REPO/releases` ← بعد ما تعمل tag

---

## 📁 هيكل المشروع

```
camera_app/
├── lib/
│   └── main.dart              ← كل كود الـ app
├── android/
│   ├── app/
│   │   ├── build.gradle
│   │   └── src/main/
│   │       ├── AndroidManifest.xml
│   │       └── kotlin/.../MainActivity.kt
│   └── build.gradle
├── .github/
│   └── workflows/
│       └── build.yml          ← GitHub Actions CI/CD
└── pubspec.yaml
```

---

## 🔑 Permissions المطلوبة

| الإذن | السبب |
|-------|-------|
| `CAMERA` | لالتقاط الصور |
| `WRITE_EXTERNAL_STORAGE` | لحفظ الصور (Android < 10) |
| `READ_EXTERNAL_STORAGE` | للقراءة (Android < 13) |
