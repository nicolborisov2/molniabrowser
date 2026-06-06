# Молния — Android TV

Полноценный браузер для Android TV Box с движком Chromium. Проект находится на стадии разработки.

## Структура проекта

```
MolniaBrowser/
├── app/
│   ├── src/main/
│   │   ├── java/com/tvbrowser/app/
│   │   │   ├── activities/
│   │   │   │   ├── MainActivity.kt        ← Главный экран (TV Leanback)
│   │   │   │   ├── BrowserActivity.kt     ← Браузер + управление пультом
│   │   │   │   ├── BookmarksActivity.kt   ← Закладки
│   │   │   │   ├── SettingsActivity.kt    ← Настройки
│   │   │   │   └── AboutActivity.kt       ← О браузере
│   │   │   ├── adapters/
│   │   │   │   └── BookmarkAdapter.kt
│   │   │   ├── models/
│   │   │   │   ├── Bookmark.kt            ← Room entity
│   │   │   │   └── AppDatabase.kt         ← Room DB + DAO
│   │   │   └── utils/
│   │   │       ├── SearchEngine.kt        ← Поисковики + UrlUtils
│   │   │       └── PrefsManager.kt        ← SharedPreferences
│   │   ├── res/
│   │   │   ├── layout/                    ← XML разметки экранов
│   │   │   ├── values/                    ← strings, colors, styles, dimens
│   │   │   ├── drawable/                  ← selectors для фокуса TV
│   │   │   └── xml/preferences.xml        ← настройки PreferenceFragment
│   │   └── AndroidManifest.xml
│   └── build.gradle
└── build.gradle
```

## Требования

- Android 10+ (API 29)
- Android TV / TV Box с пультом ДУ
- Интернет-соединение

## Ключевые функции

| Функция | Реализация |
|---|---|
| Движок Chromium | Системный WebView (обновляется автоматически) |
| Управление пультом | D-pad → скролл страницы, OK → клик |
| Навигационная панель | Кнопка BACK → панель с URL + 5 кнопок |
| Режим инкогнито | Отдельная сессия без истории и cookie |
| Закладки | Room Database, сетка 4×N |
| Поисковики | Google, Яндекс (ya.ru), DuckDuckGo |
| Настройки | JS, Cookie, размер текста, домашняя страница, очистка |
| О браузере | Версия Chromium из WebView User-Agent |

## О движке Chromium

Браузер использует **Android System WebView** — это официальный компонент Google,
основанный на Chromium и обновляемый через Google Play независимо от Android.
На Android 10+ это отдельное приложение ("Android System WebView"), которое
можно обновить до последней версии в Play Store.

Версию Chromium можно посмотреть в разделе **"О браузере"** приложения.

## Настройка поисковиков

- **Google** → `https://www.google.com/search?q=`
- **Яндекс** → `https://ya.ru/search/?text=`
- **DuckDuckGo** → `https://duckduckgo.com/?q=`

## Управление пультом в браузере

| Кнопка | Действие |
|---|---|
| ↑ ↓ ← → | Скролл страницы |
| OK / Enter | Клик на элемент |
| BACK | Открыть/закрыть навигационную панель |
| В панели: ← | Назад |
| В панели: → | Вперёд |
| В панели: 🏠 | Домой (главный экран) |
| В панели: ↺ | Обновить страницу |
| В панели: ★ | Добавить в закладки |
