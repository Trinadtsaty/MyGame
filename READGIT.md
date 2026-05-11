# 🧭 Гайд по работе с Git в Visual Studio Code

Этот гайд поможет тебе быстро начать работать с Git в VS Code: создать репозиторий, связать его с GitHub, делать коммиты, пушить, переключать ветки и клонировать проект на новом устройстве.

## 📦 1. Настройка (один раз)

### Установи Git (если не установлен)

- Скачай с [официального сайта](https://git-scm.com/downloads)
- При установке оставляй настройки по умолчанию (кроме выбора редактора — можно оставить VSCode)

### Настрой имя и email (один раз на компьютере)

```bash
git config --global user.name "Твоё Имя"
git config --global user.email "твоя_почта@example.com"
```

### Проверь настройки

```bash
git config --global --list
```

## 🆕 2. Начать новый проект (локально → на GitHub)

### VS Code (терминал открыть: `` Ctrl + ` ``)

```bash
# 1. Перейди в папку проекта
cd путь/к/папке

# 2. Инициализируй Git
git init

# 3. Создай файл .gitignore (чтобы не заливать лишнее)
echo ".vscode/
.env
__pycache__/
node_modules/" > .gitignore

# 4. Добавь все файлы в первый коммит
git add .

# 5. Сделай первый коммит
git commit -m "Initial commit"
```

### На GitHub (в браузере)

1. Нажми **New repository**
2. Напиши имя (совпадает с папкой проекта)
3. **Не** ставь галочки "Add README", ".gitignore", "license"
4. Нажми **Create repository**

### Свяжи локальный репозиторий с GitHub

```bash
git remote add origin https://github.com/ТВОЙ_АККАУНТ/НАЗВАНИЕ_РЕПОЗИТОРИЯ.git
git branch -M main
git push -u origin main
```

> Если запрашивает пароль — используй **токен** (GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate → поставить галочки `repo`, `workflow`)

## 📥 3. Клонировать проект на новом устройстве

### В первый раз:

```bash
git clone https://github.com/ТВОЙ_АККАУНТ/НАЗВАНИЕ_РЕПОЗИТОРИЯ.git
cd НАЗВАНИЕ_РЕПОЗИТОРИЯ
```

> В VS Code: `Ctrl + Shift + P` → `Git: Clone`

После клонирования у тебя уже есть связанный репозиторий. Можно сразу работать.

## 🔁 4. Повседневная работа (коммиты и пуш)

```bash
# 1. Посмотреть, что изменилось
git status

# 2. Добавить все изменения в «индекс»
git add .

# 3. Сделать коммит (снапшот)
git commit -m "Краткое описание изменений"

# 4. Отправить изменения на GitHub
git push
```

> Если работаешь с веткой, отличной от main: `git push origin название_ветки`

## 🌿 5. Ветки (branches)

### Создать новую ветку и переключиться на неё

```bash
git checkout -b новая-ветка
```

### Переключиться между ветками

```bash
git checkout main
git checkout новая-ветка
```

### Посмотреть список веток

```bash
git branch
```

### Отправить новую ветку на GitHub

```bash
git push -u origin новая-ветка
```

> Ключ `-u` связывает локальную ветку с удалённой. После этого можно просто `git push`.

### Слить ветку с main

```bash
# Перейди в main
git checkout main

# Обнови main (важно!)
git pull

# Слей
git merge новая-ветка

# Запушь
git push
```

## 🧹 6. Полезные команды

| Команда | Что делает |
|---------|-------------|
| `git log --oneline` | Показать историю коммитов (кратко) |
| `git diff` | Показать неподтверждённые изменения |
| `git pull` | Скачать изменения с GitHub (перед началом работы) |
| `git reset --hard HEAD` | Отменить все локальные изменения (осторожно!) |
| `git branch -d имя_ветки` | Удалить локальную ветку |
| `git push origin --delete имя_ветки` | Удалить ветку на GitHub |

## ⚠️ Частые ошибки

### `fatal: not a git repository`

Значит, ты не в папке с `.git`. Проверь `git status` и путь.

### `Updates were rejected because the remote contains work that you do not have`

Сначала сделай `git pull`, потом `git push`.

### `fatal: refusing to merge unrelated histories`

Если появляется при первом `git pull`:

```bash
git pull origin main --allow-unrelated-histories
```

## 📁 Структура после выполненного гайда

```
твой_проект/
├── .git/
├── .gitignore
├── README.md (этот файл)
└── (все твои файлы)
```

---

## 💡 Короткая памятка (шпаргалка)

```bash
git add .               # подготовить всё
git commit -m "текст"   # зафиксировать
git push                # отправить на GitHub
```

```bash
git pull                # скачать изменения с GitHub
git checkout -b новая   # создать и переключиться на ветку
```
