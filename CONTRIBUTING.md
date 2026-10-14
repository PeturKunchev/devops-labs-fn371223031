# Contributing / Как допринасяме

## Branches / Клони

- Never commit directly to `main`. It is protected. / Никога не комитваме директно в `main`. Той е защитен.
- One task = one Issue = one branch = one PR. / Една задача = един Issue = един клон = един PR.
- Name format / Формат на името: `<type>/<task>-<short-description>`
  - `docs/t04-runbook`
  - `docs/t07-glossary`
  - `fix/t14-revert-port`
- Allowed types / Позволени типове: `docs`, `fix`, `feat`, `chore`.
- Lowercase letters, digits and hyphens only. / Само малки латински букви, цифри и тирета.

Start every task from an up-to-date `main` / Всяка задача започва от актуален `main`:

```bash
git switch main
git pull
git switch -c docs/t00-example
```

## Commits / Комити

- Format / Формат: `<type>: <what changed>`, e.g. `docs: add glossary terms A-C`.
- Imperative mood, in English, up to 72 characters. / Повелително наклонение, на английски, до 72 знака.
- One logical change per commit. / Една логическа промяна на комит.
- Co-authored work ends with / Съвместна работа завършва с:
  `Co-authored-by: Name <email>`

## Pull Requests

- Title / Заглавие: same format as commits. / Същият формат като комитите.
- Description contains `Closes #<issue>`. / Описанието съдържа `Closes #<issue>`.
- Add a label and milestone `v0.2.0`. / Слагаме label и milestone `v0.2.0`.
- At least 1 approval from the partner (Code Owner). / Поне 1 одобрение от партньора (Code Owner).
- The author does not merge without approval. / Авторът не слива без одобрение.
- Conflicts are resolved by the author of the PR. / Конфликтите се решават от автора на PR-а.
- Delete the branch after merging. / Клонът се изтрива след сливане.

Branching strategy: TBD