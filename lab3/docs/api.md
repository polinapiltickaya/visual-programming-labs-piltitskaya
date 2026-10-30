# Документация API Connector (lab3)

В рамках лабораторной работы через плагин **Bubble API Connector** подключен внешний REST API сервис [JSONPlaceholder](https://jsonplaceholder.typicode.com/) для работы с разделом «Внешний журнал впечатлений (API)».

---

## Общая информация
* **Base URL:** `https://jsonplaceholder.typicode.com`
* **Формат данных:** `JSON`
* **Авторизация:** Не требуется (Public API)

---

## Эндпоинты (CRUD)

### 1. GET — Получение всех заметок
* **Название вызова в Bubble:** `Get All Notes`
* **HTTP Метод:** `GET`
* **URL:** `https://jsonplaceholder.typicode.com/posts`
* **Назначение:** Загрузка списка внешних заметок и публикаций для отображения в интерфейсе приложения.
* **Пример ответа (200 OK):**
```json
[
  {
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati...",
    "body": "quia et suscipit\nsuscipit recusandae..."
  }
]
```

---

### 2. POST — Создание новой заметки
* **Название вызова в Bubble:** `Create Note`
* **HTTP Метод:** `POST`
* **URL:** `https://jsonplaceholder.typicode.com/posts`
* **Headers:** `Content-Type: application/json`
* **Тело запроса (Body):**
```json
{
  "title": "<title_input>",
  "body": "<body_input>",
  "userId": 1
}
```
* **Назначение:** Отправка пользовательской заметки из формы UI на внешний сервер.
* **Пример ответа (201 Created):**
```json
{
  "title": "Новая заметка",
  "body": "Текст впечатления",
  "userId": 1,
  "id": 101
}
```

---

### 3. PUT — Обновление существующей заметки
* **Название вызова в Bubble:** `Update Note`
* **HTTP Метод:** `PUT`
* **URL:** `https://jsonplaceholder.typicode.com/posts/1`
* **Headers:** `Content-Type: application/json`
* **Тело запроса (Body):**
```json
{
  "id": 1,
  "title": "<updated_title>",
  "body": "<updated_body>",
  "userId": 1
}
```
* **Назначение:** Полное обновление данных выбранной заметки.
* **Пример ответа (200 OK):**
```json
{
  "id": 1,
  "title": "Обновленный заголовок",
  "body": "Обновленный текст",
  "userId": 1
}
```

---

### 4. DELETE — Удаление заметки
* **Название вызова в Bubble:** `Delete Note`
* **HTTP Метод:** `DELETE`
* **URL:** `https://jsonplaceholder.typicode.com/posts/1`
* **Назначение:** Отправка запроса на удаление записи по её идентификатору.
* **Пример ответа (200 OK):**
```json
{}
```

---

## Скриншоты конфигурации и UI
* `../screenshots/11-api-config-1.jpeg` — Конфигурация GET-запроса
* `../screenshots/11-api-config-2.jpeg` — Конфигурация POST-запроса
* `../screenshots/11-api-config-3.jpeg` — Конфигурация PUT-запроса
* `../screenshots/11-api-config-4.jpeg` — Конфигурация DELETE-запроса
* `../screenshots/11-api-ui.jpeg` — Отображение полученных через API данных в Repeating Group приложения