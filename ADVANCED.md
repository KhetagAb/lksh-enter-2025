## ADVANCED — Продвинутая часть

Для выполнения продвинутой части необходимо **ОБЯЗАТЕЛЬНО** выполнить BASE. Продвинутая часть является логическим продолжением.

#### Описание дополнительных endpoints:

- `POST /login` — регистрирует твой токен в системе

В теле запроса обязательно необходимо указать JSON следующего формата:
```json
{
 "reason": "причина почему мы должны взять вас в параллель P, ограничение 256 символов"
}
```


- `GET /goals?match_id=<id матча>` — список голов в конкретном матче (доступен только после регистрации токена ручкой /login)
```json
[
  {"id": 1, "player": 56, "match": 1, "minute": 42}
]
```

**Важно**: Этот endpoint доступен только после вызова /login с вашим токеном.

### Пункты задания:

Помните, что каждый пункт оценивается независимо, выполняйте только те пункты, которые вам интересны и реализация которых вам известна. 

Рекомендуется самостоятельно изучить концепты на уровне, необходимом для выполнения задания.

1. **Создать HTTP-сервер** со следующими JSON API эндпоинтами:
    - `GET /stats?team_name=<name>` — выдает статистику команды
    - `GET /versus?player1_id=<id>&player2_id=<id>` — выдает информацию о противостоянии игроков
    - Как в базовой версии задания, только теперь не консольное приложение, а HTTP-сервер

2. **Реализовать endpoint** `GET /goals?player_id=<id>`, который возвращает список всех голов игрока в формате:
```json
[
    {
        "match": 123,
        "time": 42
    },
    ...
]
```

3. **Создать HTML представление**, дополнить следующими endpoint'ами:
    - `GET /front/stats` — красивый HTML-интерфейс для статистики команд
    - `GET /front/versus` — красивый HTML-интерфейс для сравнения игроков
    - Верста и оформления на ваше усмотрение, главное чтобы было человеко-читаемо

4. **Организация кода**:
    - Вынесение общей логики в отдельные функции/классы
    - Консольная и веб версии должны по минимуму использовать дублирующий код

5. **Документация API**:
    - Создать OpenAPI-схему для всех реализованных эндпоинтов
    - Описать форматы запросов и ответов

6. **БОНУС — Отказоустойчивость**:
    - Представьте, что кто-то выдернул питание у Ваше и Нашего серверов. Ваше приложение перезапустилось, а наш сервер нет. Необходимо, чтобы ваше приложение после перезапуска отвечала на запросы, не запрашивая данные с нашего сервера, а использовала последние полученные данные.
      - Использовать постоянное хранилище данных
      - Обеспечить работу приложения при недоступности основного API

Если вы знаете что такое спецификация OpenAPI, то можете посмотреть [схему данных](schema.yaml).

## Критерии оценки

Мы будем оценивать не только работоспособность решения, но и технологическое исполнение и выбранные инструменты для разработки.

В целом, мы не против использования разных языков программирования и фреймворков, но рекомендуем выполнять работы на Python/Go. 

В продвинутой версии мы будем обращать внимание на:
- Корректность работы HTTP-сервера
- Структура и чистота кода
- Качество HTML-интерфейсов
- Качество документации
- Реализация отказоустойчивости
- Обработку ошибок веб-сервера и приложения
- Логирование
