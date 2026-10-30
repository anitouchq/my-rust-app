# 🦀 my-rust-app
<img width="1674" height="500" alt="image" src="https://github.com/user-attachments/assets/48a50e21-b648-4504-9661-04514f0aaa7e" />

Учебный проект: **CI-пайплайн на GitHub Actions** для Rust-приложения.

---

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

<img width="1193" height="749" alt="image" src="https://github.com/user-attachments/assets/3cc6f28e-6148-476c-a6f5-518c10e1334f" />

```text
Hello from Rust in Docker! 🦀
```

---

## 🏗️ Стек

* **Rust** (edition 2021)
* **Cargo**
* **rustfmt** / **clippy**
* **Docker** — multi-stage сборка
* **GitHub Actions** — CI

---

## 📄 Лицензия

**MIT** — свободно для учебных целей.
