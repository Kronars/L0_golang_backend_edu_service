# Тестовое задание

**В БД:**  
Развернуть локально postgresql 
Создать свою бд  
Настроить своего пользователя.  
Создать таблицы для хранения полученных данных. 
 
**В сервисе:** 
1. Подключение и подписка на канал в nats-streaming 
2. Полученные данные писать в Postgres 
3. Так же полученные данные сохранить in memory в сервисе (Кеш) 
4. В случае падения сервиса восстанавливать Кеш из Postgres 
5. Поднять http сервер и выдавать данные по id из кеша 
6. Сделать простейший интерфейс отображения полученных данных, для  
их запроса по id 
 
 
Доп инфо:   
• Данные статичны, исходя из этого подумайте насчет модели хранения    
в Кеше и в pg. Модель в файле model.json   
• В канал могут закинуть что угодно, подумайте как избежать проблем из-за этого   
• Чтобы проверить работает ли подписка онлайн, сделайте себе  
отдельный скрипт, для публикации данных в канал  
• Подумайте как не терять данные в случае ошибок или проблем с  
сервисом   
• Nats-streaming разверните локально ( не путать с Nats )

## Результатg

### Основная логика

`App/stan` - подключение к nats, получение сообщений, валидация

`App/db` - подключение, создание таблиц, все запросы

`App/cache` - выполнение запросов, сериализация

`App/front` - html и js скрипты

### Скрипты:

`Scripts/PsqlInit.sh` - создание пользователя, бд

`Scripts/NatsStartup.sh` - запуск nats-streaming

`Scripts/spam2stan.go` - спам случайно сгенерированными данными

## Модель данных:

![Здесь должна быть картиночка](%D0%9C%D0%BE%D0%B4%D0%B5%D0%BB%D1%8C%20%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85.png)
