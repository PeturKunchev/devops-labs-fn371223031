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