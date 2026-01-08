# Explore With Me Plus

![Java](https://img.shields.io/badge/Java-21-007396?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.3.0-6DB33F?logo=springboot)
![Hibernate](https://img.shields.io/badge/Hibernate-6.5.2.Final-59666C?logo=hibernate)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-336791?logo=postgresql)
![Docker](https://img.shields.io/badge/Docker-20.10+-2496ED?logo=docker&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.9.9-C71A36?logo=apache-maven&logoColor=white)
![Lombok](https://img.shields.io/badge/Lombok-1.18.32-green?logo=lombok)
![MapStruct](https://img.shields.io/badge/MapStruct-1.5.5.Final-red)

Explore With Me Plus — платформа для обмена информацией об интересных событиях. Пользователи могут публиковать мероприятия, искать их по различным фильтрам и находить компанию для участия. Это групповой проект, разработанный командой:  
[vBoltunov](https://github.com/vBoltunov), [TireNik](https://github.com/TireNik), [AlionaKulikova](https://github.com/AlionaKulikova).  

Приложение построено на микросервисной архитектуре: основной сервис отвечает за бизнес-логику, сервис статистики - за сбор и предоставление данных о просмотрах.

## Основные возможности
- Поиск и просмотр событий с фильтрами (текст, категории, даты, платность, доступность, популярность).
- Создание и модерация событий, управление заявками на участие.
- Комментарии к событиям (с ограничениями по участию) и подписки на пользователей/категории.
- Администрирование: управление категориями, подборками, событиями, пользователями и комментариями.
- Статистика просмотров и хитов событий.
- Разделённые API: публичные, приватные и административные.

## Технологии
- **Backend**: Java 21, Spring Boot 3.3.0, Hibernate 6.5.2
- **Библиотеки**: MapStruct 1.5.5, Lombok 1.18.32, Jakarta Validation 3.0.2
- **Базы данных**: PostgreSQL 16 (продакшн), H2 (тесты)
- **Инфраструктура**: Docker 20.10+, Maven 3.9.9

## Структура проекта
- **main-service** — основной модуль с подмодулями:  
  `category`, `comment`, `compilation`, `events`, `requests`, `subscriptions`, `user`
- **stats-service** — сбор статистики (подмодули `stat-dto`, `stat-client`, `stat-server`)
- Отдельные базы PostgreSQL для каждого сервиса

## Установка и запуск
### Требования
- **Java 21** (любой совместимый дистрибутив: Amazon Corretto, Eclipse Temurin, OpenJDK)
- **Maven 3.9+** (протестировано на 3.9.9)
- **Docker Engine 20.10+**
- **Docker Compose 2.0+**

**Примечание:** 
- Для локальной разработки используется Amazon Corretto 21.0.3
- В Docker-контейнерах используется образ `eclipse-temurin:21-jdk-alpine`

### Инструкция
1. Клонировать репозиторий  
   ```bash
   git clone https://github.com/vBoltunov/java-explore-with-me-plus.git
   cd java-explore-with-me-plus
   ```

2. Собрать проект  
   ```bash
   mvn clean install
   ```

3. Запустить в контейнерах  
   ```bash
   docker-compose up --build -d
   ```

   Доступ:  
   - Основной сервис: http://localhost:8080  
   - Сервис статистики: http://localhost:9090

## Документация API
Спецификации OpenAPI доступны только в виде файлов:
- [Основной сервис](ewm-main-service-spec.json)
- [Сервис статистики](ewm-stats-service-spec.json)

**Примечание:** Swagger UI не настроен в этом проекте. Используйте IntelliJ IDEA или онлайн Swagger Editor для просмотра документации.

## Тестирование
- Готовые коллекции Postman для основного и статистического сервисов.
- Интерактивное тестирование через спецификации в IDEA.
