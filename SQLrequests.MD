# Инструкция по написанию SQL запросов

## Основные принципы

### 1. Структура запроса
```sql
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column1;
```

### 2. Ключевые команды

| Команда | Описание |
|---------|----------|
| SELECT | Выбор данных |
| FROM | Указание таблицы |
| WHERE | Фильтрация условиями |
| JOIN | Объединение таблиц |
| GROUP BY | Группировка данных |
| ORDER BY | Сортировка результатов |

### 3. Примеры запросов

**Простой выбор:**
```sql
SELECT * FROM users;
```

**С условиями:**
```sql
SELECT name, email FROM users WHERE age > 18;
```

**С объединением:**
```sql
SELECT u.name, o.order_id 
FROM users u
JOIN orders o ON u.id = o.user_id;
```

### 4. Лучшие практики
- Используйте заглавные буквы для команд SQL
- Давайте понятные имена таблицам и столбцам
- Добавляйте комментарии для сложных запросов
- Тестируйте запросы перед использованием в продакшене
## 5. Расширенные техники

### Подзапросы
```sql
SELECT name FROM users 
WHERE id IN (SELECT user_id FROM orders WHERE total > 100);
```

### Агрегатные функции
```sql
SELECT COUNT(*), AVG(salary), MAX(salary)
FROM employees
GROUP BY department;
```

### Транзакции
```sql
BEGIN TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

### Индексы
```sql
CREATE INDEX idx_email ON users(email);
DROP INDEX idx_email;
```

## 6. Частые ошибки

- Забывают добавить условие в WHERE при массовых операциях
- Используют SELECT * вместо конкретных столбцов
- Не оптимизируют запросы для больших объёмов данных
- Забывают использовать LIMIT для ограничения результатов

## 7. Дополнительные ресурсы

- [SQL Documentation](https://www.sql.org)
- Практикуйтесь на реальных базах данных
- Изучайте план выполнения запросов (EXPLAIN)
