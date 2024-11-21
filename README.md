# GIT
---
## С чего начать  
* Ознакомиться с понятием **системы контроля версий**  
* Установка ПО на ПК с официального [сайта](https://git-scm.com/downloads)  
* Если работаешь на Windows настоятельно рекомендую в региональных настройках системы установить галочку на использование кодировки UTF-8. Это избавит тебя от трудностей, возникающих при использовании кирииллицы в директориях.  
* Изучить основные команды для навигации по файловой системе и созданию/удалению файлов/папок с использованием командной строки  
## Основные команды  
- Инициализация репозитория  
```bash
git init
```
- Проверка состояния репозитория  
```bash
git status
```
- Добавление файлов в репозиторий  
```bash
git add <*имя фала или флаг --all, если нужно добавить все файлы в папке*>
```
- Коммит  
```bash
git commit -m 'сообщение'
```
Дополнительные возможности команды:  
```bash
git commit -a -m "Сообщение коммита"
```
То же самое, что последовательное выполнение **git add .** и **git commit -m "Сообщение коммита"** за исключением того, что команда не добавляет в отслеживаемую зону новые (untracked) файлы.  
```bash
git commit -amend -m "Сообщение коммита"
```
Дополняет последний коммит, добавляя в него "свежие" изменения. Также, меняет сообщение последнего коммита. Новый коммит не создается.  
- Просмотр истории коммитов  
```bash
git log
```
- Получить сокращённый лог
```bash
git log --oneline
```
- Генерация SSH-ключа  
```bash
ssh-keygen -t ed25519 -C "электронная почта"
```
- Привязка ключа к GitHub и проверка правильности ключа командой  
```bash
ssh -T git@github.com
```
- Привязка удалённого репозитория к локальному  
```bash
git remote add origin git@github.com:%имя-аккаунта%/first-project.git
```
- Проверка связанности репозиториев  
```bash
git remote -v
```
- Синхронизация локального репозитория с удалённым  
```bash
git push -u origin main
```
- Получение файлов из удалённого репозитория  
```bash
git pull origin main
```
- Клонирование удалённого репозитория в папку
```bash
git clone <git@github.com:...>
```
## Команды для работы с изменениями и ветками  
- Просмотр изменений  
```bash
git diff
```
Показывает разницу между текущим *неотслеживаемым* состоянием  
```bash
git diff --staged
```
Показывает разницу между текущим *отслеживаемым* состоянием  
```bash
git diff COMMIT_ID
```
Показывает разницу между текущим состоянием и указанным снимком  
- Отмена/сброс изменений  
Данную команду стоит исполнять очень внимательно, т.к. она может быть использована для переписания истории. Вызывается с разными параметрами.  
```
git reset [**--soft|--mixed|--hard**] [**commit**]
```
**Режимы команды:**  
* --hard  
Самая "сильная" вариация, удаляет коммиты безвозвратно.  
* --mixed  
Возвращает проект к указанному коммиту, при этом переводит все коммиты после указанного в **неотслеживаемую (unstaged)** зону.  
* --soft  
Возвращает проект к указанному коммиту, при этом переводит все коммиты после указанного в **отслеживаемую (staged)** зону.  
**Желаемый коммит:**  
* Может использоваться хеш коммита;
* Могут использваться различные вариации с *HEAD* (**^** - назад на один коммит, **^^** - назад на два коммита и т.д. или **~n**, где n - количество коммитов).  
- Перемещение между коммитами  
```bash
git checkout [hash|HEAD~n|main]
```
Для перемещения между версиями файлов можно использовать следующий синтаксис команды:  
```bash
git checkout <указатель коммита> -- путь_до_файла_1 путь_до_файла_2
```
Для возврата файла к версии в последнем коммите:  
```bash
git checkout -- путь_до_файла_1 путь_до_файла_2
```
Работает только для **неотслеживаемых** (**untracked** или **modified**) изменений.  
- Удаление **неотслеживаемых** Файлов из репозитория
```bash
git clean <параметры>
```
## Структура  
### Что хранится в папке .git  
- файл HEAD  
в нём хранится ссылка на последний коммит  
HEAD - указывает на актуальную версию проекта. Обычно это последний коммит, но этот указатель можно смещать.  
### Статусы  
* untracked  
неотслеживаемые файлы
* tracked  
отслеживаемые файлы, которые были зафиксированы с помощью commit или add
* staged (indexed, cached)  
подготовленный (после выполнения команды git add)
* modified