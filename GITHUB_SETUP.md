# 📚 دليل إعداد GitHub - منصة المسابقات الرياضية
# GitHub Setup Guide - Math Competition Platform

## 🎯 نظرة عامة

هذا الدليل سيساعدك في رفع مشروع منصة المسابقات الرياضية على GitHub وربطه مع Railway للنشر التلقائي.

---

## 📋 المتطلبات الأساسية

✅ **قبل البدء تأكد من وجود:**
- حساب GitHub ([إنشاء حساب](https://github.com/join))
- Git مثبت على جهازك ([تحميل Git](https://git-scm.com/downloads))
- مشروع منصة المسابقات جاهز ويعمل محلياً

---

## 🚀 الخطوة 1: إعداد Git محلياً

### تكوين Git (إذا لم يتم من قبل):
```bash
git config --global user.name "اسمك هنا"
git config --global user.email "your.email@example.com"
```

### التحقق من الإعداد:
```bash
git config --global user.name
git config --global user.email
```

---

## 📁 الخطوة 2: تحضير المشروع

### التأكد من وجود الملفات المطلوبة:
```bash
# في مجلد المشروع، تأكد من وجود:
ls -la

# يجب أن ترى:
# ✅ .gitignore
# ✅ requirements.txt
# ✅ Procfile
# ✅ railway.toml
# ✅ runtime.txt
# ✅ README.md
# ✅ manage.py
```

### إنشاء repository محلي:
```bash
# في مجلد المشروع
git init
git add .
git commit -m "🚀 Initial commit - Math Competition Platform"
```

---

## 🌐 الخطوة 3: إنشاء Repository على GitHub

### الطريقة الأولى: عبر موقع GitHub
1. اذهب إلى [github.com](https://github.com)
2. سجل دخولك
3. انقر على **"New repository"** (الزر الأخضر)
4. املأ المعلومات:
   - **Repository name**: `math-competition-platform`
   - **Description**: `منصة تفاعلية للمسابقات الرياضية - Interactive Math Competition Platform`
   - **Visibility**: Public (أو Private حسب رغبتك)
   - **لا تحدد** "Add a README file" (لأن لديك واحد بالفعل)
5. انقر على **"Create repository"**

### الطريقة الثانية: عبر GitHub CLI (اختياري)
```bash
# تثبيت GitHub CLI أولاً
# ثم تسجيل الدخول
gh auth login

# إنشاء repository
gh repo create math-competition-platform --public --description "منصة تفاعلية للمسابقات الرياضية"
```

---

## 🔗 الخطوة 4: ربط المشروع المحلي مع GitHub

```bash
# إضافة remote origin
git remote add origin https://github.com/YOUR_USERNAME/math-competition-platform.git

# تحديد الفرع الرئيسي
git branch -M main

# رفع الكود لأول مرة
git push -u origin main
```

**استبدل `YOUR_USERNAME` باسم المستخدم الخاص بك على GitHub**

---

## 📝 الخطوة 5: تحديث README.md

قم بتحديث الروابط في ملف README.md:

```markdown
# استبدل هذه الروابط في README.md:
- GitHub Repository: https://github.com/YOUR_USERNAME/math-competition-platform
- Issues: https://github.com/YOUR_USERNAME/math-competition-platform/issues
- Railway Deploy: https://railway.app/new/template/django
```

---

## 🏷️ الخطوة 6: إضافة Tags والإصدارات

```bash
# إنشاء tag للإصدار الأول
git tag -a v1.0.0 -m "🎉 الإصدار الأول - منصة المسابقات الرياضية"
git push origin v1.0.0
```

---

## 📊 الخطوة 7: إعداد GitHub Pages (اختياري)

لعرض الوثائق:

1. اذهب إلى **Settings** في repository
2. انتقل إلى **Pages**
3. اختر **Source**: Deploy from a branch
4. اختر **Branch**: main
5. اختر **Folder**: / (root)
6. انقر **Save**

---

## 🔄 الخطوة 8: إعداد GitHub Actions (اختياري)

إنشاء ملف `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Railway

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up Python
      uses: actions/setup-python@v3
      with:
        python-version: '3.13'
        
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
        
    - name: Run tests
      run: |
        python manage.py test
```

---

## 🚀 الخطوة 9: ربط مع Railway

### الطريقة الأولى: عبر موقع Railway
1. اذهب إلى [railway.app](https://railway.app)
2. سجل دخولك باستخدام GitHub
3. انقر **"New Project"**
4. اختر **"Deploy from GitHub repo"**
5. اختر repository المشروع
6. Railway سيقوم بالنشر تلقائياً!

### الطريقة الثانية: عبر Railway CLI
```bash
# تثبيت Railway CLI
npm install -g @railway/cli

# تسجيل الدخول
railway login

# ربط المشروع
railway link

# نشر المشروع
railway up
```

---

## 📱 الخطوة 10: اختبار النشر

بعد النشر الناجح:

1. **تحقق من الرابط**: `https://yourapp.railway.app`
2. **اختبر الوظائف الأساسية**:
   - دخول التلاميذ برمز `ben25`
   - إنشاء مسابقة جديدة
   - حل الأسئلة
   - عرض النتائج

---

## 🔄 تحديث المشروع مستقبلاً

```bash
# إضافة التغييرات
git add .

# إنشاء commit
git commit -m "✨ وصف التحديث هنا"

# رفع التحديث
git push origin main

# Railway سيقوم بالنشر التلقائي
```

---

## 🛡️ أفضل الممارسات

### الأمان:
- ✅ لا ترفع ملفات `.env` أو كلمات المرور
- ✅ استخدم `.gitignore` بشكل صحيح
- ✅ استخدم متغيرات البيئة للمعلومات الحساسة

### التنظيم:
- ✅ استخدم commit messages واضحة
- ✅ أنشئ branches للميزات الجديدة
- ✅ استخدم Pull Requests للمراجعة

### الوثائق:
- ✅ حدث README.md بانتظام
- ✅ أضف تعليقات واضحة في الكود
- ✅ وثق أي تغييرات مهمة

---

## 🔧 استكشاف الأخطاء

### مشاكل شائعة:

#### خطأ في الـ push:
```bash
# إذا رفض GitHub الـ push
git pull origin main --rebase
git push origin main
```

#### مشاكل الصلاحيات:
```bash
# استخدام Personal Access Token
# اذهب إلى GitHub Settings > Developer settings > Personal access tokens
# أنشئ token جديد واستخدمه بدلاً من كلمة المرور
```

#### مشاكل Railway:
- تحقق من متغيرات البيئة
- راجع سجلات النشر
- تأكد من صحة ملف `railway.toml`

---

## 📞 الدعم

إذا واجهت مشاكل:

1. **GitHub Issues**: [إنشاء issue جديد](https://github.com/YOUR_USERNAME/math-competition-platform/issues)
2. **وثائق GitHub**: [docs.github.com](https://docs.github.com)
3. **وثائق Railway**: [docs.railway.app](https://docs.railway.app)

---

## 🎉 تهانينا!

الآن لديك:
- ✅ مشروع على GitHub
- ✅ نشر تلقائي على Railway
- ✅ موقع إلكتروني يعمل
- ✅ نظام تحديث سهل

**🚀 مشروعك الآن جاهز للعالم! 🌍**

---

## 📋 قائمة تحقق نهائية

- [ ] Repository منشور على GitHub
- [ ] README.md محدث بالروابط الصحيحة
- [ ] Railway متصل ويعمل
- [ ] متغيرات البيئة معدة
- [ ] التطبيق يعمل على الرابط المباشر
- [ ] جميع الوظائف تعمل بشكل صحيح

**🎯 استمتع بمشاركة مشروعك مع العالم! 🚀**
