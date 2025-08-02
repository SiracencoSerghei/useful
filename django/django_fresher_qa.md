
# Python Django Fresher / Junior – Питання та Відповіді

## 1. Python – Основи

### Які основні типи даних у Python?
int, float, str, bool, list, tuple, dict, set.

### Різниця між `==` і `is`?
`==` порівнює значення об’єктів, `is` перевіряє, чи це той самий об’єкт у пам’яті.

### Що таке list comprehension?
Короткий синтаксис для створення списків:  
```python
nums = [x**2 for x in range(5)]
```

### Для чого потрібні *args і **kwargs?
`*args` – передача довільної кількості позиційних аргументів у функцію.  
`**kwargs` – передача довільної кількості іменованих аргументів.

### Що таке __init__ та __str__ у класах?
`__init__` – конструктор класу, викликається при створенні об’єкта.  
`__str__` – метод для повернення рядкового представлення об’єкта.

### Як відкрити файл у Python?
```python
with open("file.txt", "r") as f:
    content = f.read()
```

---

## 2. Django – Основи

### Що таке MVT?
Model – робота з даними, View – логіка, Template – відображення. Django автоматично з’єднує їх.

### Що таке Django ORM?
Інструмент для взаємодії з БД через Python-код замість SQL.

### Як створити проект і додаток?
```bash
django-admin startproject myproject
python manage.py startapp blog
```

### Що таке міграції?
Система відстеження змін у моделях для автоматичного оновлення структури БД.

### Різниця між ForeignKey і ManyToManyField?
- `ForeignKey` – зв’язок один-до-багатьох.  
- `ManyToManyField` – зв’язок багато-до-багатьох.

### Як створити REST API у Django?
Використати Django REST Framework: створити серіалізатор, viewset, додати URL.

---

## 3. SQL

### Основні запити SQL?
- `SELECT` – вибір даних  
- `INSERT` – додавання  
- `UPDATE` – оновлення  
- `DELETE` – видалення  
- `JOIN` – об’єднання таблиць

### Як підключити PostgreSQL у Django?
У `settings.py` змінити `DATABASES`:
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
Файл, який вказує, які файли Git повинен ігнорувати.

---

## 5. Security

### Що таке CSRF?
Захист від підроблених запитів з іншого сайту. Django має вбудований CSRF-токен.

### Як захиститися від SQL Injection?
Використовувати ORM, а не сирі SQL-запити.

---

## 6. Поради на співбесіду

- Розкажи про навчальні проекти (To-Do App, Blog).
- Поясни, як працює MVT.
- Покажи код на GitHub.
- Будь впевнений, навіть якщо досвіду немає – підкресли, що швидко вчишся.
