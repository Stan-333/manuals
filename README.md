#GIT
---
##С чего начать
*Ознакомиться с понятием **системы контроля версий**
*Установка ПО на ПК с официального [сайта](https://git-scm.com/downloads)
*Если работаешь на Windows настоятельно рекомендую в региональных настройках системы установить галочку на использование кодировки UTF-8. Это избавит тебя от трудностей, возникающих при использовании кирииллицы в директориях.
*Изучить основные команды для навигации по файловой системе и созданию/удалению файлов/папок с использованием командной строки
##Основные команды
-Инициализация репозитория
```bash
git init
```
-Проверка состояния репозитория
```bash
git status
```
-Добавление файлов в репозиторий
```bash
git add <*имя фала или флаг --all, если нужно добавить все файлы в папке*>
```
-Коммит
```bash
git commit -m 'сообщение'
```
-Просмотр истории коммитов
```bash
git log
```
-Генерация SSH-ключа
```bash
ssh-keygen -t ed25519 -C "электронная почта"
```
-Привязка ключа к GitHub и проверка правильности ключа командой
```bash
ssh -T git@github.com
```
-Привязка удалённого репозитория к локальному
```bash
*git remote add* origin git@github.com:%имя-аккаунта%/first-project.git
```
-Проверка связанности репозиториев
```bash
git remote -v
```
-Синхронизация локального репозитория с удалённым
```bash
git push -u origin main
```