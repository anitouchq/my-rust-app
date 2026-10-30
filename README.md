# 🦀 my-rust-app

## 📖 О проекте

Простое Rust-приложение, для которого настроен CI-пайплайн.
При каждом `push` и `pull request` в ветки `main` / `master` автоматически:

* 🧹 проверяется форматирование через **rustfmt**
* 🧪 прогоняется линтер **clippy** (с `-D warnings`)
* 🏗️ собирается debug и release билд
* ✅ запускаются тесты через `cargo test`
* 🐳 собирается **Docker-образ** (multi-stage: rust → debian-slim) и сохраняется как артефакт

---

## ⚙️ Как работает пайплайн

| Job | Что делает |
| :--- | :--- |
| **lint** | `cargo fmt --check`, `cargo clippy` |
| **test** | `cargo check`, `cargo build` (debug + release), `cargo test` |
| **docker-build** | сборка образа, сохранение артефакта, тестовый запуск |

---

## 🐳 Проверка локально

```bash
docker build -t my-rust-app:latest .
docker run --rm my-rust-app:latest
```

**Ожидаемый вывод:**

<img width="1583" height="994" alt="photo_5413821073230340030_w" src="https://github.com/user-attachments/assets/42925452-995c-4b2f-aa7a-4d76e90049a2" />

```text
Hello from Rust in Docker! 🦀
```

---

## 🏗️ Стек

* **Rust** (edition 2021)
* **Cargo**
* **rustfmt** / **clippy**
* **Docker** — multi-stage сборка
---

## 📄 Лицензия

**MIT** — свободно для учебных целей.
