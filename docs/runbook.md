# Runbook

## Start locally / Локално стартиране

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\Activate.ps1
pip install -r requirements.txt
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

## Check that it works / Проверка, че работи

Open / Отворете: http://localhost:8000/health

Expected / Очаквано: status `200` and body `{"status": "ok"}`.

From the terminal / От терминала:

```bash
curl -i http://localhost:8000/health
```

## Run the tests / Тестове

```bash
pip install pytest
pytest
```

All tests must pass. / Всички тестове трябва да минат.

## When something breaks / Когато нещо се счупи

1. Is the service running and on the right port? / Работи ли услугата и на правилния порт ли е?

```bash
   curl -i http://localhost:8000/health
```

   Linux/macOS: `lsof -i :8000`. Windows: `netstat -ano | findstr :8000`.

2. Are the dependencies installed in the active environment? / Инсталирани ли са зависимостите в активната среда?

```bash
   pip install -r requirements.txt
```

3. What changed recently? / Какво е променено наскоро?

```bash
   git log --oneline -5
```

   If a commit broke it, revert it / Ако комит го е счупил, отменете го:

```bash
   git revert <sha>
```

## Run with Docker

Build the image:

```bash
docker build -t notes-api:0.3.0 .
```

Run the container:

```bash
docker run -d --name notes-api -p 8000:8000 notes-api:0.3.0
```

Check the health endpoint:

```bash
curl http://localhost:8000/health
```

View the container logs:

```bash
docker logs notes-api
```

Stop and remove the container:

```bash
docker rm -f notes-api
```

## Run with Docker Compose

### Configure environment variables

Copy `.env.example` to `.env` and set the PostgreSQL credentials. The `.env` file is excluded from Git and must not be committed.

### Start the application

Build the application image and start the application and database:

```bash
docker compose up -d --build
```

### Check running services

```bash
docker compose ps
```

The database should report `healthy` once its healthcheck succeeds.

### View application logs

```bash
docker compose logs -f app
```

Press `Ctrl+C` to stop following the logs.

### Stop services

```bash
docker compose down
```

This stops and removes the containers and network while preserving the named database volume.

To also remove the named volume and its persisted database data:

```bash
docker compose down -v
```

Use this command only when you intend to delete the stored database data.

### Optional database administration

Start Adminer using the `tools` profile:

```bash
docker compose --profile tools up -d
```

Open port `8081` in GitHub Codespaces. Select PostgreSQL as the system, use `db` as the server, and enter the credentials configured in `.env`.
