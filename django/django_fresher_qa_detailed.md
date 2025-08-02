
# Python Django Fresher / Junior – Питання та Відповіді з прикладами коду

## 1. Python – Основи

### Які основні типи даних у Python?
- int: ціле число (`x = 10`)
- float: число з плаваючою комою (`pi = 3.14`)
- str: рядок (`name = "Serghei"`)
- bool: логічний тип (`flag = True`)
- list: список (`nums = [1, 2, 3]`)
- tuple: кортеж (`coords = (10, 20)`)
- dict: словник (`user = {"name": "Ana", "age": 25}`)
- set: множина (`unique = {1, 2, 3}`)

### Різниця між `==` і `is`?
```python
a = [1, 2]
b = [1, 2]
print(a == b)  # True – значення однакові
print(a is b)  # False – різні об'єкти в пам'яті
```

### Що таке list comprehension?
```python
nums = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]
```

### Для чого потрібні *args і **kwargs?
```python
def demo(*args, **kwargs):
    print("args:", args)
    print("kwargs:", kwargs)

demo(1, 2, 3, name="Ana", age=25)
# args: (1, 2, 3)
# kwargs: {'name': 'Ana', 'age': 25}
```

### Що таке __init__ та __str__ у класах?
```python
class Person:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Person: {self.name}"

p = Person("Ana")
print(p)  # Person: Ana
```

### Як відкрити файл у Python?
```python
with open("file.txt", "w") as f:
    f.write("Hello")

with open("file.txt", "r") as f:
    print(f.read())
```

---

## 2. Django – Основи

### Що таке MVT?
- **Model**: взаємодія з БД
- **View**: бізнес-логіка
- **Template**: HTML-шаблони
```python
# models.py
from django.db import models
class Post(models.Model):
    title = models.CharField(max_length=100)

# views.py
from django.shortcuts import render
from .models import Post
def post_list(request):
    posts = Post.objects.all()
    return render(request, "posts.html", {"posts": posts})

# templates/posts.html
{% for post in posts %}
    <h2>{{ post.title }}</h2>
{% endfor %}
```

### Що таке Django ORM?
```python
# Отримати всі об'єкти
Post.objects.all()
# Фільтрувати
Post.objects.filter(title__contains="Django")
# Додати новий
Post.objects.create(title="New Post")
```

### Як створити проект і додаток?
```bash
django-admin startproject myproject
cd myproject
python manage.py startapp blog
```

### Що таке міграції?
```bash
python manage.py makemigrations
python manage.py migrate
```

### Різниця між ForeignKey і ManyToManyField?
```python
class Author(models.Model):
    name = models.CharField(max_length=50)

class Book(models.Model):
    author = models.ForeignKey(Author, on_delete=models.CASCADE)  # один-до-багатьох
    co_authors = models.ManyToManyField(Author, related_name="co_books")  # багато-до-багатьох
```

### Як створити REST API у Django?
```python
# serializers.py
from rest_framework import serializers
from .models import Post
class PostSerializer(serializers.ModelSerializer):
    class Meta:
        model = Post
        fields = '__all__'

# views.py
from rest_framework import viewsets
class PostViewSet(viewsets.ModelViewSet):
    queryset = Post.objects.all()
    serializer_class = PostSerializer

# urls.py
from rest_framework.routers import DefaultRouter
router = DefaultRouter()
router.register(r'posts', PostViewSet)
urlpatterns = router.urls
```

---

## 3. SQL

### Основні запити SQL?
```sql
SELECT * FROM posts;
INSERT INTO posts (title) VALUES ('Hello');
UPDATE posts SET title='Updated' WHERE id=1;
DELETE FROM posts WHERE id=1;
```

### Як підключити PostgreSQL у Django?
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'mydb',
        'USER': 'myuser',
        'PASSWORD': 'mypassword',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

---

## 4. Git

### Як створити репозиторій і зробити commit?
```bash
git init
git add .
git commit -m "First commit"
```

### Як створити нову гілку?
```bash
git checkout -b feature
```

### Що таке .gitignore?
```gitignore
*.pyc
__pycache__/
db.sqlite3
.env
```

---

## 5. Security

### Що таке CSRF?
Cross-Site Request Forgery – атака, коли зловмисник надсилає запит від імені користувача. Django додає `{% csrf_token %}` у форми.

### Як захиститися від SQL Injection?
Використовувати ORM замість сирих SQL-запитів:
```python
Post.objects.filter(title="Django")
```

---

## 6. Поради на співбесіду

- Підготуй демо-проект на GitHub (To-Do App, Blog).
- Вчи MVT на пам’ять – це часто питають.
- Практикуй створення моделей, в’юшок, шаблонів.
- Не бійся казати, що вчив самостійно – це плюс.
