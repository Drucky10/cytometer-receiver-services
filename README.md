# Cytometer Receiver — desktop app (releases)

Публичный репозиторий для **скачивания** настольного приложения **Cytometer Receiver v3**
(приём и обработка данных гематологических анализаторов Mindray BC‑3200, ABX Micros ES 60 и др.).
Исходный код — в приватном репозитории; здесь только готовые сборки (`.exe`) и руководство.

## Скачать и установить

1. Откройте **[Releases](../../releases)** и скачайте последний **`CytometerReceiver.exe`**.
2. Запустите его **от имени администратора** (правый клик → «Запуск от имени администратора») —
   права нужны для перезапуска COM‑порта. Устанавливать больше ничего не нужно
   (Python и всё необходимое уже внутри).
3. Войдите: адрес сервера `http://<адрес‑сервера>:8000`, ваш e‑mail и пароль.

📖 **[Руководство пользователя](cytometer-receiver-user-manual/user_manual_v3.html)**

**Требования:** Windows 10 / 11 (64‑бит), 4 ГБ ОЗУ, свободный COM‑порт (драйвер **CH340**
для Mindray), права **администратора**, сеть до сервера лаборатории (порт **8000**).

---

## Для мейнтейнера — как выпустить новую версию

`.exe` собирается автоматически из приватного репозитория `Drucky10/cytometer-receiver`
и публикуется в **Releases** этого (публичного) репозитория.

**Однократная настройка (нужен доступ к приватным исходникам):**
1. Создайте **Personal Access Token** (Settings → Developer settings → Tokens) с правом
   чтения приватного репозитория (classic: scope `repo`; fine‑grained: `Contents: Read`
   для `Drucky10/cytometer-receiver`).
2. В **этом** репозитории: **Settings → Secrets and variables → Actions → New repository
   secret**, имя **`SOURCE_TOKEN`**, значение — токен.

**Выпуск релиза:**
- Вкладка **Actions → «Build & release v3 .exe» → Run workflow**, введите версию
  (например `v3.0.0`). Workflow заберёт исходники из приватного репо, соберёт
  `CytometerReceiver.exe` и приложит его к новому Release с этим тегом.

**Первый релиз можно сделать и вручную** (без токена): вкладка **Releases → Draft a new
release → тег `v3.0.0`**, приложите готовый `CytometerReceiver.exe` (см. `build.bat` в
приватном репозитории или `cytometer-receiver-client/dist/CytometerReceiver.exe` после
локальной сборки) и опубликуйте.
