﻿---
layout: default
title: ROLLBACK DELTA
nav_order: 28
parent: Запросы SQL+
grand_parent: Справочная информация
has_children: false
has_toc: false
---

# ROLLBACK DELTA

Запрос позволяет откатить горячую [дельту](../../../overview/main_concepts/delta/delta.md) — 
вернуть [логическую базу данных](../../../overview/main_concepts/logical_db/logical_db.md) 
в состояние, которое предшествовало изменениям этой дельты. Перед выполнением запроса необходимо 
определить логическую базу данных, [используемую по умолчанию](../../../working_with_system/other_features/default_db_set-up/default_db_set-up.md), 
если она еще не определена. Если существуют незавершенные операции загрузки данных, то откат выполнить невозможно. При выполнении ROLLBACK все успешно завершенные операции откатятся.

В ответе возвращается:
*   объект ResultSet c одной записью, содержащей номер последней закрытой дельты, при успешном выполнении 
    запроса;
*   исключение при неуспешном выполнении запроса.

При успешном выполнении запроса все изменения данных горячей дельты отменяются и зарезервированный ранее 
номер горячей дельты освобождается; номер последней закрытой дельты не изменяется.

**Примечание:** откат закрытой дельты невозможен.

## Синтаксис

```sql
ROLLBACK DELTA
```