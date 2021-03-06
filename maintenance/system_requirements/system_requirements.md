---
layout: default
title: Минимальные системные требования
nav_order: 1
parent: Эксплуатация
has_children: false
has_toc: false
---

# Минимальные системные требования

Система предъявляет следующие минимальные требования:
*   аппаратные требования:
    *   ядро системы: 4 CPU, 16 RAM, 20 HDD;
    *   сервис мониторинга статусов Kafka: 2 CPU, 8 RAM, 20 HDD;
*   программные требования:
    *   ADB версии 6.15.0;
    *   ADQM версии 20.4.4.18;
    *   ADG версии 2.7.2;
    *   ADS:
        *   ADS версии 1.5;
        *   Kafka версии 2.4;
        *   Zookeeper версии 3.5.6.
    
Компоненты, с которыми работает система, предъявляют минимальные требования, перечисленные 
в таблице ниже.

| Компонент | Системные требования
|:-|:-
| ADB | <https://docs.arenadata.io/adb/requirements/online.html#id2>
| ADQM | <https://docs.arenadata.io/adqm/requirements/index.html#clickhouse>
| ADG (Tarantool) | <https://www.tarantool.io/en/sizing_calculator/>
| Kafka | <https://docs.arenadata.io/ads/Requirements/min.html>
| Zookeeper | <https://docs.arenadata.io/ads/Requirements/min.html> 