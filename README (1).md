# 🎬 Кінобаза — Інформаційна система оцінювання фільмів

> Аналог IMDb · JavaFX + JDBC + PostgreSQL  
> Сумський державний університет, гр. ІН-31/1 — 2026

---

## 👥 Команда

| Роль | ПІБ |
|---|---|
| 🟡 Team Lead | Яценко Іван Олександрович |
| 🔵 Developer 1 | Самков Данило Олександрович |
| 🔵 Developer 2 | Цебро Нікіта Олександрович |

Науковий керівник: П'ятаченко В. Ю., асистент кафедри КН

---

## 📋 Про проєкт

Локальна система обліку фільмів та глядацьких оцінок (варіант 2 КР БД).  
Рейтинг фільму рахується лише якщо проголосувало **більше 10 глядачів**, інакше = 0.

**Стек:** Java 17 · JavaFX · JDBC · PostgreSQL · Maven  
**Архітектура:** MVC (Model / View FXML / Controller / DAO)

---

## 🗄️ Схема БД

5 таблиць: `genre`, `country`, `movie`, `viewer`, `rating`

```
genre (genre_name PK)
country (country_name PK, exists)
movie (movie_id PK, genre FK, country FK, movie_name, release_year)
viewer (viewer_id PK, name)
rating (viewer_id PK FK, movie_id PK FK, raiting)
```

---

## 📅 План робіт

| № | Завдання | Хто |
|---|---|---|
| 1 | Maven-структура, pom.xml, .gitignore | Team Lead |
| 2 | SQL-скрипти: таблиці + тестові дані | Team Lead |
| 3 | Entity-класи: Movie, Viewer, Rating | Developer 1 |
| 4 | Entity-класи: Genre, Country + db.properties | Developer 2 |
| 5 | JDBCHelper + підключення до БД | Team Lead |
| 6 | DAO: MovieDao, RatingDao (CRUD) | Developer 1 |
| 7 | DAO: ViewerDao, GenreDao, CountryDao | Developer 2 |
| 8 | Бізнес-логіка: рейтинг, пошук, аналітика | Team Lead |
| 9 | JavaFX: головний екран, TableView | Developer 1 |
| 10 | JavaFX: форма додавання/редагування, валідація | Developer 2 |
| 11 | JavaDoc → папка docs/ | Team Lead |
| 12 | Тестування і фінальний коміт | Всі |

---

## 🌿 Гілки

```
main       ← стабільна версія (тільки через Pull Request)
develop    ← основна розробка
feature/*  ← окремі задачі
fix/*      ← виправлення
```

**Правила:**
- В `main` — тільки через Pull Request, який перевіряє Team Lead
- Кожна задача = окрема гілка `feature/назва`
- Гілка видаляється після злиття

---

## ✍️ Коміти

Формат: `тип(область): опис англійською`

```bash
feat(entity): add Movie class with getters and setters
feat(dao): implement MovieDao CRUD with PreparedStatement
feat(javafx): add TableView on main screen
fix(rating): return 0 when voters less than 10
docs(readme): update project description
chore(pom): add JavaFX and PostgreSQL JDBC dependency
```

Типи: `feat` `fix` `docs` `refactor` `chore`  
Мінімум **5 комітів** від кожного учасника.

---

## 🚀 Запуск

```bash
# 1. Клонувати
git clone https://github.com/MaikHilton/Java-Team-Project.git

# 2. Створити БД
psql -U postgres -c "CREATE DATABASE kinobase;"
psql -U postgres -d kinobase -f sql/01_create_tables.sql

# 3. Налаштувати src/main/resources/db.properties
db.url=jdbc:postgresql://localhost:5432/kinobase
db.user=postgres
db.password=YOUR_PASSWORD

# 4. Запустити
mvn clean compile
mvn javafx:run
```
