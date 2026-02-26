# Flask, основы

## 1. Установка и начальная настройка

```bash
# Создание виртуального окружения
python -m venv venv

# Активация виртуального окружения
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Установка Flask
pip install flask
```

## 2. Структура проекта

```
flask_project/
│
├── app.py                 # Основной файл приложения
├── requirements.txt       # Зависимости(не обязательно)
├── config.py              # Конфигурация (не обязательно)
│
├── templates/             # HTML шаблоны
│   ├── base.html
│   ├── login.html
│   ├── dashboard.html
│   └── admin.html
│
└── static/                # CSS, JavaScript, изображения
     └── css/

```

## 3. Базовый код
```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def home():
    if request.method == 'POST':
        name = request.form.get('name')
        return f"Hello, {name}!"
    return render_template('home.html')

if __name__ == '__main__':
    app.run(debug=True)
```

### html шаблон
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
</head>
<body>
    <form method="POST">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required>
        <br>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required>
        <br>
        <button type="submit">Login</button>
    </form>
</body>
</html>
```