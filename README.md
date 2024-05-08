# 🐱‍👤 Kittygram

**Kittygram** - это веб-приложение, представляющее собой социальную сеть для любителей кошек.

## Описание

Здесь пользователи могут создавать профили своих питомцев, загружать их фотографии, указывать информацию о котах (имя, цвет, дата рождения), а также отмечать их достижения и умения.

### Основные возможности:

- Регистрация и аутентификация пользователей
- Создание, редактирование и удаление профилей котов
- Загрузка фотографий питомцев
- Добавление новых достижений в общий справочник
- Просмотр профилей чужих котов и их достижений

## Использованные технологии

- Python 3.9, Django 3.2, Django REST Framework, PostgreSQL, Docker, Docker-Compose, Nginx, Gunicorn
- Pillow (для обработки изображений), Djoser (для аутентификации), Python-dotenv (для работы с переменными окружения)
- JSON, YAML, Postman (для тестирования API)

Данный проект демонстрирует навыки создания полнофункционального веб-приложения с использованием Django, работы с базами данных, обработки изображений, аутентификации пользователей, развертывания проекта в Docker-контейнерах и взаимодействия с API.

## Как запустить проект на сервере:
 - Клонируем проект git@github.com:EvgeniiChichin/kittygram_final.git
 - Подключаемся к удаленному серверу и создаем на нем папку под названием kittygram
 - Устанавливаем Nginx
   ```
   sudo apt install nginx -y
   sudo systemctl start nginx
   ```
 - Через редактор Nano открываем файл конфигурации веб-сервера и вписываеми необходимые настройки:
   ```
   sudo nano /etc/nginx/sites-enabled/default
   ```
 - Проверияем корректность настроек Nginx:
   ```
   sudo nginx -t
   ```
 - Перезапускаем Nginx:
   ```
   sudo service nginx reload
   ```
 - Устанавливаем Cerbot и получаем SSL-сертификат
   ```
   sudo apt install snapd
   sudo certbot --nginx
   ```
- Копируем файлы docker-compose.yml и .env (создаем и заполняем по примеру показанному в файле .env.example) в папку проекта kittygram
- Запускаем Docker Compose на сервере в режиме демона
  ```
  sudo docker compose -f docker-compose.yml up -d
  ```
- Проверяем все ли контейнеры запущены
  ```
  sudo docker compose -f docker-compose.yml ps
   ```
- Выполните миграции, соберите статические файлы бэкенда и скопируйте их в /backend_static/static/:
  ```
  sudo docker compose -f docker-compose.yml exec backend python manage.py migrate
  sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
  sudo docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/ 
  ```

## Автор
* [Евгений Чичин](https://github.com/EvgeniiChichin)
