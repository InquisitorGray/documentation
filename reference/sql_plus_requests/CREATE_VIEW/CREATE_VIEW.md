---
layout: default
title: CREATE VIEW
nav_order: 15
parent: Запросы SQL+
grand_parent: Справочная информация
has_children: false
has_toc: false
---

# CREATE VIEW

Запрос позволяет создать или заменить [логическое представление](../../../overview/main_concepts/logical_view/logical_view.md) 
в [логической базе данных](../../../overview/main_concepts/logical_db/logical_db.md).

В ответе возвращается:
*   пустой объект ResultSet при успешном выполнении запроса;
*   исключение при неуспешном выполнении запроса.

## Синтаксис

Создание логического представления:
```sql
CREATE VIEW [db_name.]view_name AS SELECT query
```

Создание логического представления с заменой существующего представления, если такое будет найдено:
```sql
CREATE OR REPLACE VIEW [db_name.]view_name AS SELECT query
```

## Параметры

*   `db_name` — имя логической базы данных, в которой создается или заменяется логическое представление. 
    Указывается опционально, если выбрана логическая БД, 
    [используемая по умолчанию](../../../working_with_system/other_features/default_db_set-up/default_db_set-up.md);
*   `view_name` — имя создаваемого или заменяемого логического представления. В запросе на создание 
    представления имя должно быть уникально среди логических сущностей логической БД;
*   `query` — [SELECT](../SELECT/SELECT.md)-подзапрос, на основе которого строится логическое представление.

## Ограничения

В подзапросе `query` не допускается использование:
*   логических представлений,
*   [системных представлений](../../system_views/system_views.md) 
    `INFORMATION_SCHEMA`,
*   директивы [FOR SYSTEM_TIME](../SELECT/SELECT.md#sect_for_system_time),
*   секции `DATASOURCE_TYPE`.

## Пример

```sql
CREATE VIEW sales.stores_by_sold_products AS
  SELECT store_id, SUM(product_units) AS product_amount
  FROM sales.sales
  GROUP BY store_id
  ORDER BY product_amount DESC
  LIMIT 20
```