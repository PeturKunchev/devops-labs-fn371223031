# Service / Услугата

> Fill in every TODO. / Попълнете всяко TODO.

## Purpose / Предназначение

TODO: two or three sentences: what the service does and for whom. / две-три изречения: какво прави услугата и за кого.

## Endpoints / Адреси

| Method | Path | What it does / Какво прави |
|---|---|---|
| GET | /health | Проверка дали приложението работи: `{"status": "ok"}` |
| GET | /version | Версията от променливата на средата APP_VERSION (по подразбиране 0.1.0) |
| GET | /notes | Списък с всички бележки |
| POST | /notes | Създава бележка. title е задължително (от 1 до 100 знака), body не е |
| GET | /notes/{id} | Една бележка; 404, ако не съществува |

## Dependencies / Зависимости

TODO: what the service needs in order to run. / какво е нужно на услугата, за да работи.
