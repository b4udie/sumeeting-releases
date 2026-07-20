# SuMeeting — Releases

**SuMeeting** записує дзвінки в Google Meet (аудіо + відео), локально транскрибує їх
(NVIDIA Canary-1b-v2, укр/англ) і генерує summary та action points через Claude Code.
Все працює на твоєму Mac — аудіо нікуди не завантажується (опційно можна ввімкнути AssemblyAI).

> Це репозиторій лише для дистрибуції. Сорс-код — у приватному репо.

## Завантаження

| Компонент | Де взяти |
|-----------|----------|
| macOS-застосунок | 👉 **[Останній реліз](../../releases/latest)** → `SuMeeting.dmg` (підписаний і нотаризований Apple) |
| Chrome-розширення | 👉 **[Chrome Web Store](https://chromewebstore.google.com/detail/sumeeting/olciponfpbfpaohpjclonfebcmaeeghd)** |

## Вимоги

- **macOS 13+** на **Apple Silicon** (M1 і новіші)
- **Google Chrome** (для розширення)
- ~4 ГБ вільного місця (модель транскрипції завантажується при першому запуску)
- Підписка Claude (Pro/Max) для summary — апка проведе через логін Claude Code

## Встановлення

1. Відкрий `SuMeeting.dmg` і перетягни **SuMeeting** у **Applications**.
2. Запусти SuMeeting — при першому запуску він запропонує:
   - вибрати рушій транскрипції (локальний Canary або AssemblyAI з API-ключем);
   - завантажити модель (для локального рушія);
   - залогінитись у Claude Code (для summary / action points).
3. Встанови розширення [з Chrome Web Store](https://chromewebstore.google.com/detail/sumeeting/olciponfpbfpaohpjclonfebcmaeeghd).

## Використання

1. Запусти **SuMeeting.app** (він тримає локальний бекенд).
2. Зайди в дзвінок Google Meet.
3. Натисни іконку розширення → **Start recording** (дай дозвіл на мікрофон при першому разі).
4. Після дзвінка натисни **Stop** — запис піде на обробку, транскрипція і summary
   з'являться в застосунку SuMeeting.
