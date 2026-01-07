### Bu README ushbu loyihamga mos emas bu shunchaki project yaratishda o'zgartirishlar kiritish uchun o'zim uchun qisqacha note hisoblanadi!
---

# Django Starter Project

Bu loyiha **Django’ni to‘g‘ri strukturada o‘rganish** uchun yaratilgan.
Project `apps/` yondashuvi asosida qurilgan va real loyihalar uchun mos.

---

## 📁 Project Structure

```text
django-first-project/
│
├── core/                  # Asosiy project (settings, urls)
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
├── apps/                  # Barcha app’lar shu yerda bo‘ladi
│   └── blogs/
│       ├── migrations/
│       ├── admin.py
│       ├── apps.py
│       ├── models.py
│       ├── views.py
│       └── urls.py        # ⚠️ Qo‘lda yaratiladi
│
├── templates/              # Global templates papkasi
│   └── base.html
│
├── venv/                   # Virtual environment
├── manage.py
└── README.md
```

---

## ⚙️ O‘rnatish va sozlash

### 1️⃣ Virtual environment yaratish

```bash
python -m venv venv
```

Aktivatsiya:

```bash
source venv/Scripts/activate
```

---

### 2️⃣ Django o‘rnatish

```bash
pip install django
```

---

### 3️⃣ Project yaratish

```bash
django-admin startproject core .
```

---

### 4️⃣ App’lar uchun papka

```bash
mkdir apps
```

---

### 5️⃣ App yaratish

```bash
python manage.py startapp blogs apps/blogs
```

> Django `urls.py` ni avtomatik yaratmaydi, shuning uchun qo‘lda yaratamiz.

---

### 6️⃣ blogs/urls.py

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='blogs-index'),
]
```

---

### 7️⃣ blogs/views.py

```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Blogs app is working")
```

---

### 8️⃣ App’ni settings.py ga qo‘shish

```python
INSTALLED_APPS = [
    ...
    'apps.blogs.apps.BlogsConfig',
]
```

---

### 9️⃣ Templates sozlash

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates'],
        'APP_DIRS': True,
    },
]
```

> `templates/` ichida qo‘shimcha papkalar bo‘lsa ham o‘zgartirish shart emas.

---

### 🔗 URL ulash

**core/urls.py**

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('blogs/', include('apps.blogs.urls')),
]
```

---

### 🗄️ Migratsiyalar

```bash
python manage.py migrate
```

---

### ▶️ Serverni ishga tushirish

```bash
python manage.py runserver
```

* Blogs → [http://127.0.0.1:8000/blogs/](http://127.0.0.1:8000/blogs/)
* Admin → [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

---

## ⚠️ Muhim eslatmalar

* `urls.py` — **har bir app’da qo‘lda yaratiladi**
* `apps/` struktura — **tavsiya etiladigan yondashuv**
* `404 /` va `favicon.ico` — xato emas
* `BigAutoField` — default primary key

---

## 🎯 Maqsad

Bu loyiha:

* Django asoslarini to‘g‘ri o‘rganish
* Katta loyihalarga tayyor bo‘lish
* Toza arxitektura bilan ishlash

---
