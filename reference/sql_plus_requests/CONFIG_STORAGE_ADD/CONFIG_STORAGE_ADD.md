---
layout: default
title: CONFIG_STORAGE_ADD
nav_order: 9
parent: Запросы SQL+
grand_parent: Справочная информация
has_children: false
has_toc: false
---

# CONFIG_STORAGE_ADD

Запрос позволяет подключить к системе источник данных — [СУБД](../../../introduction/supported_DBMS/supported_DBMS.md) 
указанного типа. После успешного выполнения запроса можно 
[создавать](../CREATE_TABLE/CREATE_TABLE.md) [логические таблицы](../../../overview/main_concepts/logical_table/logical_table.md) 
с размещением данных в этой СУБД и [загружать](../INSERT_INTO_logical_table/INSERT_INTO_logical_table.md) 
данные в нее.

**Примечание:** перед выполнением запроса необходимо добавить параметры СУБД 
в [конфигурацию](../../../maintenance/configuration/configuration.md) системы.

В ответе возвращается:
*   пустой объект ResultSet при успешном выполнении запроса;
*   исключение при неуспешном выполнении запроса.

При успешном выполнении запроса все [логические базы данных](../../../overview/main_concepts/logical_db/logical_db.md) 
[окружения](../../../overview/main_concepts/environment/environment.md) 
активируются для указанной СУБД [хранилища](../../../overview/main_concepts/data_storage/data_storage.md). 
При этом копирование логических таблиц и их данных из других СУБД хранилища не происходит и не может быть 
выполнено средствами системы.

## Синтаксис

```sql
CONFIG_STORAGE_ADD('datasource_alias')
```

## Параметры

*   `datasource_alias` — псевдоним СУБД хранилища. Возможные значения: `adb`, `adqm`, `adg`.

## Пример

Подключение ADB к хранилищу:
```sql
CONFIG_STORAGE_ADD('adb')
```