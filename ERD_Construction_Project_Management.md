# ERD: Система управления продажами квартир (Brusnika)

```mermaid
erDiagram
    PROJECT ||--|{ APARTMENT : содержит
    APARTMENT ||--o{ CONTRACT : продаётся
    CLIENT ||--o{ CONTRACT : подписывает

    PROJECT {
        int id PK
        string name
        string address
        string status
    }

    APARTMENT {
        int id PK
        int project_id FK
        string type
        int floor
        decimal area
        decimal price
        string status
    }

    CLIENT {
        int id PK
        string fio
        string phone
        string email
        string status
    }

    CONTRACT {
        int id PK
        int apartment_id FK
        int client_id FK
        decimal total_price
        string status
        datetime signed_date
    }
```

### Статусы

| Сущность | Поле | Значения |
|----------|------|----------|
| PROJECT | status | `in_progress`, `completed` |
| APARTMENT | status | `available`, `reserved`, `sold` |
| CONTRACT | status | `draft`, `signed`, `completed` |
| CLIENT | status | `lead`, `prospect`, `client`, `owner` |
