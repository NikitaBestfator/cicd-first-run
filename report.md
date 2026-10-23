# Отчёт по практике CI

## 1. Ссылки на запуски
- Красный запуск (break stylesheet link): https://github.com/NikitaBestfator/cicd-first-run/actions/runs/39951097506
- Зелёный запуск (restore stylesheet link): https://github.com/NikitaBestfator/cicd-first-run/actions/runs/39951335238

## 2. Прогноз и факт
- Прогноз до поломки: упадёт test_stylesheet_exists, Build site и Save site artifact не выполнятся.
- Фактический результат: https://github.com/NikitaBestfator/cicd-first-run/actions/runs/39951097506/job/120405472796,
упал test_stylesheet_exists с ошибкой Missing stylesheet: missing.css, job остановился с exit code 1.

## 3. Упавший тест и причина
- Тест: test_stylesheet_exists
- Строка причины: Missing stylesheet: missing.css

## 4. Что стало с шагами сборки и артефакта
- Build site: не выполнен (job остановился на Run tests)
- Save site artifact: не выполнен

## 5. Где выполнялись тесты и почему результат на GitHub
Тесты выполнялись на runner (виртуальной машине), предоставленной GitHub Actions.
Результат сохранён на GitHub (в логах запуска), потому что workflow запускался
на инфраструктуре GitHub. Это обеспечивает воспроизводимость: любой участник
проекта может открыть Actions и увидеть, что проверялось для конкретного коммита.

## 6. Почему зелёный результат после смены аудитории не доказывает отсутствие ошибки
Тесты не проверяют конкретное значение аудитории (301 vs 302). Они проверяют
только наличие файлов и структуру. Поэтому зелёный результат доказывает лишь то,
что проверки не покрывают эту логику, а не то, что 302 — правильный номер.
