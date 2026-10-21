# Здача WS6

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: OleksandrMartynov
- Ваше репо: https://github.com/OleksandrMartynov/property-workflows
- SHA: 1293dabf1283baef8e2ce33bfc3154c0584a3a1c
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://property-workflows-rho.vercel.app

## PM

—

## Розробник

- Рядок «Вимоги:» з `docs/conformance.md` на SHA: Вимоги: https://github.com/solomchaak/property-workflows-spec · джерело: issues · знімок 2026-10-21
- Перший PR «Оновлення вимог»: https://github.com/OleksandrMartynov/property-workflows/pull/3
- Журнал `docs/spec-reading.md`: https://github.com/OleksandrMartynov/property-workflows/blob/1293dabf1283baef8e2ce33bfc3154c0584a3a1c/docs/spec-reading.md
- Питання в репо PM (щонайменше 3, з них щонайменше 1 — власне issue): https://github.com/solomchaak/property-workflows-spec/issues/8, https://github.com/solomchaak/property-workflows-spec/issues/9, https://github.com/solomchaak/property-workflows-spec/issues/5#issuecomment-6274129127
- PR «Специфікація» з перекладом першого зрізу: https://github.com/OleksandrMartynov/property-workflows/pull/4 — зміна add-template-runs: кожен AC PM — сценарій з тим самим ID, archive у гілці, рядки матриці
- Зміна `impl-<зріз>`: https://github.com/OleksandrMartynov/property-workflows/tree/1293dabf1283baef8e2ce33bfc3154c0584a3a1c/openspec/changes/archive/2026-10-19-impl-template-runs; після уточнень PM — https://github.com/OleksandrMartynov/property-workflows/tree/1293dabf1283baef8e2ce33bfc3154c0584a3a1c/openspec/changes/archive/2026-10-21-impl-clarify-template-runs
- PR-и задач «Реалізація» (щонайменше 2): https://github.com/OleksandrMartynov/property-workflows/pull/6, https://github.com/OleksandrMartynov/property-workflows/pull/7, https://github.com/OleksandrMartynov/property-workflows/pull/8; після уточнень PM — https://github.com/OleksandrMartynov/property-workflows/pull/13, https://github.com/OleksandrMartynov/property-workflows/pull/14; hardening за оцінками ризиків CodeRabbit — https://github.com/OleksandrMartynov/property-workflows/pull/15 (ADR 0003), https://github.com/OleksandrMartynov/property-workflows/pull/16 (RLS-політики з (select auth.uid()), тести атомарного запуску)
- PR «Оновлення вимог» після уточнень PM: https://github.com/OleksandrMartynov/property-workflows/pull/10 (знімок 2026-10-21: 12 нових AC, 4 змінені)
- PR «Специфікація» зі змінами після уточнень: https://github.com/OleksandrMartynov/property-workflows/pull/11 — зміна clarify-template-runs (ADDED / MODIFIED, ID AC PM без змін); план — https://github.com/OleksandrMartynov/property-workflows/pull/12
- AC, які ви реалізували: AC-RUN-01 (реалізовано), AC-RUN-02 (реалізовано), AC-RUN-03 (реалізовано), AC-RUN-04 (реалізовано), AC-RUN-05 (реалізовано), AC-RUN-06 (реалізовано), AC-RUN-07 (реалізовано), AC-RUN-08 (реалізовано), AC-RUN-09 (реалізовано), AC-RUN-10 (реалізовано), AC-RUN-11 (реалізовано), AC-RUN-12 (реалізовано), AC-TASK-01 (реалізовано), AC-TASK-02 (реалізовано), AC-TASK-03 (реалізовано), AC-TASK-04 (реалізовано), AC-TASK-05 (реалізовано), AC-TASK-06 (реалізовано), AC-TASK-07 (реалізовано), AC-TASK-08 (реалізовано), AC-TASK-09 (реалізовано), AC-TASK-10 (реалізовано), AC-TASK-11 (реалізовано), AC-TASK-12 (реалізовано), AC-TASK-13 (реалізовано), AC-TASK-14 (реалізовано), AC-TASK-15 (реалізовано), AC-TASK-16 (реалізовано), AC-TASK-17 (реалізовано), AC-TASK-18 (реалізовано) — усі 30 як у docs/conformance.md на SHA (`npm run ac:coverage`: 30 / 30)

## Бонус E

`/opsx:verify impl-template-runs` перед archive плану (підсумок — коментар у
https://github.com/OleksandrMartynov/property-workflows/pull/8): 0 CRITICAL, 1 WARNING, 3 SUGGESTION.

| Знахідка | Рівень | Рішення |
|---|---|---|
| D5 у `design.md`: список виконавців (`list_assignable_users`) має повертати лише `id` і `email`, а повертав ще й `role` — зайве розкриття даних профілю | WARNING | виправлено в https://github.com/OleksandrMartynov/property-workflows/pull/6: лише `id` і `email` |
| Відмова в запуску шаблону використовувала код `NOT_ALLOWED` позначки задачі — користувач бачив повідомлення про задачі | SUGGESTION | виправлено в https://github.com/OleksandrMartynov/property-workflows/pull/6: окремий код `LAUNCH_NOT_ALLOWED` у `src/lib/runs/messages.ts` |
| Немає рендер-тестів сторінок (`/runs`, `/runs/[id]`) | SUGGESTION | не додано: поведінку AC доводять тести бази на PGlite (`tests/db/`) і юніт-тести `src/lib/runs`; рендер — кандидат на e2e у WS7 |
| Після помилки валідації назва випадку повертається у формі через `?case_name=` в URL | SUGGESTION | свідомо лишено: дані синтетичні, довжину обрізано до 200 символів; для справжніх даних — передавати через cookie чи стан форми |

Що з цього випливає: `/opsx:verify` ловить розходження між `design.md` і кодом, які не бачать ні CI, ні `ac:coverage`
(AC зелені, а рішення D5 не виконано). Тому його варто запускати перед archive `impl-<зріз>`, а не після.
