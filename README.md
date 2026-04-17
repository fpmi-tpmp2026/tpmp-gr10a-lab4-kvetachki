# Flower Greenhouse System — Documentation & Project Management Repository
### Лабораторная работа №4  
**Flower Greenhouse System — Documentation, UML, Project Management, CI/CD**

---

## Description

Данный репозиторий содержит полный комплект документации, необходимый для анализа, проектирования и сопровождения командного проекта *Flower Greenhouse System*, разработанного в рамках Лабораторной работы №4.

Репозиторий включает:

- UML‑диаграммы индивидуального задания  
- UML‑диаграммы командного проекта  
- ER‑диаграмму базы данных  
- описание архитектуры приложения  
- документацию по Git‑workflow  
- Kanban‑планирование  
- CI/CD‑конвейер  
- Wiki‑раздел с подробными страницами  

Исходный код приложения расположен в отдельном репозитории и связан с данным как часть общего проектного решения.

---

## Installation

Ниже приведена корректная инструкция по установке **исходного кода приложения** (второй репозиторий).  
Документационный репозиторий установки не требует.

### Требования

- Linux / macOS / Windows (WSL)
- GCC (GNU Compiler Collection)
- SQLite3
- Make

### Шаги установки

1. Клонировать репозиторий с исходным кодом:
```bash
git clone https://github.com/tatttti/kvetachki-code.git
cd kvetachki-code
```

2. Установить SQLite3 (Ubuntu/Debian):
```bash
sudo apt-get update
sudo apt-get install sqlite3 libsqlite3-dev
```

3. Установить SQLite3 (CentOS/RHEL):
```bash
sudo yum install sqlite sqlite-devel
```

4. Установить SQLite3 (macOS):
```bash
brew install sqlite
```

5. Собрать проект:
```bash
make
```

6. Запустить приложение:
```bash
./bin/flower_greenhouse

```
### Важно:  
База данных greenhouse.db создаётся автоматически при первом запуске.
Все таблицы и дефолтные данные формируются в функции init_database().

## Usage

После успешной сборки и запуска приложения пользователь попадает в меню авторизации.  
Система поддерживает две роли: **ADMIN** и **CUSTOMER**, каждая из которых имеет собственный набор функций.

### Авторизация

При запуске программы отображается форма входа:
```bash
=== Flower Greenhouse System ===
Login: admin
Password: admin123

Welcome! Role: ADMIN
```


### Доступные роли и учетные данные

| Роль | Логин | Пароль |
|------|--------|---------|
| ADMIN | admin | admin123 |
| CUSTOMER | customer | admin123 |

---

## Основные функции приложения

### Для менеджера (ADMIN)

Менеджер имеет доступ ко всем административным функциям:

- управление цветами (добавление, изменение, удаление, поиск);
- управление композициями (CRUD);
- управление составом композиции (добавление цветов);
- управление политикой наценок (normal / 1day / 2days);
- просмотр аналитических отчётов:
  - выручка за период,
  - популярная композиция,
  - статистика по срочности,
  - использование цветов,
  - продажи композиций;
- просмотр всех заказов.

### Пример меню менеджера


```bash
=== Manager Menu ===
1. Reports
2. Flower management
3. Composition management
4. Price policy settings
0. Exit

```

### Для покупателя (CUSTOMER)

Покупатель может:

- просматривать доступные композиции;
- просматривать состав композиции;
- оформлять новый заказ;
- просматривать историю своих заказов.

#### Пример меню покупателя

```bash
=== Customer Menu ===
1. View all compositions
2. View composition details
3. View my orders
4. Create new order
0. Exit
```

---

## Пример оформления заказа

```bash
=== Customer Menu ===
1. View all compositions
2. View composition details
3. View my orders
4. Create new order
0. Exit
```

---
## Project Structure (Code Repository)  


```bash
kvetachki-code/
├── src/                    # Исходный код
│   ├── main.c
│   ├── db.c
│   ├── user.c
│   ├── flower.c
│   ├── composition.c
│   ├── order.c
│   ├── order_service.c
│   ├── price_policy.c
│   ├── report.c
│   ├── ui_customer.c
│   ├── ui_manager.c
│   └── ui_order.c
│
├── include/                # Заголовочные файлы
│   ├── db.h
│   ├── user.h
│   ├── flower.h
│   ├── composition.h
│   ├── order.h
│   ├── order_service.h
│   ├── price_policy.h
│   ├── report.h
│   └── customer.h
│
├── tests/                  # Unit-тесты
├── .github/workflows/      # CI/CD
│   └── build.yml
├── Makefile
└── greenhouse.db           # SQLite база данных
```

## Documentation Structure (This Repository)

```bash
kvetachki-docs/
├── uml/                    # UML диаграммы
│   ├── use-case/
│   ├── activity/
│   ├── sequence/
│   ├── class/
│   └── component/
│
├── db/                     # ER-диаграмма, SQL-описания
├── workflow/               # Git workflow, branching model
├── ci-cd/                  # CI/CD документация
├── kanban/                 # Скриншоты и описание Kanban
├── wiki/                   # Материалы для Wiki
└── README.md               # Этот файл

```
## Contributing

### Команда **kvetachki**

Проект разработан в составе команды из двух участников.  
Каждый участник внёс вклад в архитектуру, разработку, тестирование и документацию.

| Участник | Роль | Основные задачи |
|---------|------|-----------------|
| [Tanya Golovkova](https://github.com/tatttti) | Team Lead | Архитектура приложения, проектирование UML, ER‑диаграмма, CI/CD, документация, реализация ключевых модулей |
| [Karalina Paulouskaya](https://github.com/jl-cvyrj) | Developer | Разработка UI‑модулей, работа с базой данных, тестирование, отчёты, участие в проектировании |

### Вклад участников

- разработка архитектуры приложения и структуры репозиториев;  
- создание UML‑диаграмм всех типов (Use Case, Activity, Sequence, Class, Component);  
- проектирование и документирование базы данных;  
- реализация модулей приложения на языке C;  
- настройка GitHub Actions (CI/CD);  
- разработка Makefile и структуры проекта;  
- создание и ведение Kanban‑доски;  
- оформление Wiki‑раздела и всей документации;  
- подготовка отчётов и материалов для защиты.

---

## Source Code Repository

Исходный код приложения расположен в отдельном репозитории:
[kvetachki-code](https://github.com/tatttti/kvetachki-code.git)  


---

## Основные реализованные задачи
- проектирование архитектуры приложения
- разработка UML‑диаграмм всех типов
- создание ER‑диаграммы базы данных
- реализация всех модулей приложения
- настройка GitHub Actions
- ведение Kanban‑доски
- оформление [Wiki](https://github.com/fpmi-tpmp2026/tpmp-gr10a-lab4-kvetachki/wiki) и документации
