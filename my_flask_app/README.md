Это простое веб-приложение для редактирования профиля пользователя, созданное с использованием Flask и Flask-WTF для валидации форм. Пользователи могут обновлять свое имя, адрес электронной почты и пароль.

## Установка

1. Клонируйте репозиторий:

    ```bash
    git clone https://github.com/yourusername/edit-profile-app.git
    cd edit-profile-app
    ```

2. Создайте виртуальное окружение и активируйте его:

    ```bash
    python -m venv venv
    source venv/bin/activate  # Для Windows используйте `venv\Scripts\activate`
    ```

3. Установите необходимые зависимости:

    ```bash
    pip install -r requirements.txt
    ```

## Использование

1. Запустите Flask приложение:

    ```bash
    flask run
    ```

2. Откройте браузер и перейдите по адресу `http://127.0.0.1:5000/` для доступа к приложению.

## Файлы

- `app.py`: Основной файл вашего Flask приложения.
- `forms.py`: Файл, содержащий класс формы `EditProfileForm`.
- `templates/`: Директория, содержащая HTML-шаблоны.
- `requirements.txt`: Файл, содержащий список зависимостей.

## Пример формы

```python
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Length, Email, EqualTo, Optional

class EditProfileForm(FlaskForm):
    name = StringField('Name', validators=[DataRequired(), Length(min=2, max=20)])
    email = StringField('Email', validators=[DataRequired(), Email()])
    password = PasswordField('Password', validators=[Optional(), Length(min=6)])
    confirm_password = PasswordField('Confirm Password', validators=[Optional(), EqualTo('password', message='Passwords must match')])
    submit = SubmitField('Update Profile')
```

## Требования

- Python 3.7+
- Flask
- Flask-WTF
- WTForms

## Лицензия

Этот проект лицензирован под лицензией MIT. Подробности смотрите в файле [LICENSE](LICENSE).