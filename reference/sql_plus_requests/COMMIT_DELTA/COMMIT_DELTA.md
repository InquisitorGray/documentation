---
layout: default
title: COMMIT DELTA
nav_order: 8
parent: Запросы SQL+
grand_parent: Справочная информация
has_children: false
has_toc: false
---

# COMMIT DELTA

Запрос позволяет закрыть открытую (горячую) [дельту](../../../overview/main_concepts/delta/delta.md). 
Дата и время закрытия дельты могут быть указаны в запросе или установлены системой.

Перед выполнением запроса необходимо определить логическую базу данных, 
[используемую по умолчанию](../../../working_with_system/other_features/default_db_set-up/default_db_set-up.md), 
если она еще не определена.

В ответе возвращается:
*   объект ResultSet c одной записью, содержащей информацию о дате и времени закрытия дельты, 
    при успешном выполнении запроса;
*   исключение при неуспешном выполнении запроса.

При успешном выполнении запроса горячие записи дельты перемещаются в категорию актуальных, 
а зафиксированные ранее записи, которые больше не являются актуальными, — в категорию архивных. 
Дельта закрывается и становится недоступна для загрузки данных. Подробнее о порядке обновления записей 
см. в разделе [Физическая таблица](../../../overview/main_concepts/physical_table/physical_table.md).

В качестве даты и времени закрытия дельты устанавливаются дата и время, указанные в запросе (если они 
указаны и корректны) или определенные системой (если дата и время не указаны).

## Синтаксис

Закрытие открытой дельты:
```sql
COMMIT DELTA
```

Закрытие открытой дельты с указанными датой и временем закрытия:
```sql
COMMIT DELTA SET date_time_expression
```

## Параметры

*   `date_time_expression` — метка даты и времени вида `'YYYY-MM-DD hh:mm:ss'`. Возможные форматы см. в разделе
    [Форматы даты и времени](../../timestamp_formats/timestamp_formats.md).

## Ограничения

Если в запросе указаны дата и время закрытия дельты, они должны быть больше, чем дата и время последней 
закрытой дельты. Дату и время последней закрытой дельты можно узнать, выполнив запрос 
[GET_DELTA_OK](../GET_DELTA_OK/GET_DELTA_OK.md).

## Пример

```sql
COMMIT DELTA SET '2021-03-21 09:29:54'
```