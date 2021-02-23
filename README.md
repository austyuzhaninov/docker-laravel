# docker-laravel

Проект включает в себя следующие пакеты:
```
apache2
mariadb
adminer
composer:2.0.9
```
*Список пакетов и их версии можно устанавливать на ваш вкус и цвет*

1. В директории app клонируем свой проект с github'a

2. Собираем docker контейнер:
```
docker-compose up --build
```

3. Создаём файл `.env` для работы Laravel (копируем из `.env.example`)

4. Заходим в сервис контейнера web для генерации ключа приложения:
```
docker-compose exec web bash
```

5. Генерируем ключ:
```
php artisan key:generate
```

6. Заходим в adminer: <http://127.0.0.1:6080> (то что указали в docker-compose.yml)
7. Подключаемся к БД:
```
login: root
password: example_password
```

8. Создаём БД `example_db_name` с режимом сопоставления *utf8mb4_unicode_ci*

9. Настраиваем Laravel, указываем хост базы - это имя нашего сервиса `db`:
```
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=example_db_name
DB_USERNAME=root
DB_PASSWORD=example_password
```

10. Возвращаемся в терминал контейнера, выполняем миграцию БД:
`php artisan migrate`

Список команд:
```
docker stop ID - остановить контейнер
docker-compose up - поднять контейнеры
```

[github] <https://github.com/austyuzhaninov/docker-laravel>