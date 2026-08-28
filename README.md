# SuMeeting — Releases

**SuMeeting** записує дзвінки в Google Meet (аудіо + відео), транскрибує їх
(NVIDIA Canary-1b-v2, укр/англ — локально на твоєму Mac або на хмарному GPU) і генерує
summary та action points через Claude Code. Транскрипти й summary зберігаються локально,
записи — на Mac або в твоєму Google Drive.

> Це репозиторій лише для дистрибуції. Сорс-код — у приватному репо.
> Сайт: **https://sumeeting.aura-shield.app/** ·
> [Privacy Policy](https://sumeeting.aura-shield.app/privacy.html) ·
> [Terms](https://sumeeting.aura-shield.app/terms.html)

## Завантаження

| Компонент | Де взяти |
|-----------|----------|
| macOS-застосунок | 👉 **[Останній реліз](../../releases/latest)** → `SuMeeting.dmg` (підписаний і нотаризований Apple) |
| Chrome-розширення | 👉 **[Chrome Web Store](https://chromewebstore.google.com/detail/sumeeting/olciponfpbfpaohpjclonfebcmaeeghd)** |

## Вимоги

- **macOS 13+** на **Apple Silicon** (M1 і новіші)
- **Google Chrome** (для розширення)
- **Google-акаунт** (вхід, сховище записів у Drive, учасники з Calendar)
- ~6–7 ГБ вільного місця для локального рушія транскрипції (модель завантажується при
  першому запуску; не потрібно, якщо обираєш Cloud GPU)
- **Claude Code** (для summary / action points; можна пропустити)

## Встановлення

1. Відкрий `SuMeeting.dmg` і перетягни **SuMeeting** у **Applications**.
2. Запусти SuMeeting, увійди через Google. При першому запуску він запропонує:
   - **рушій транскрипції**: **Local** (усе на твоєму Mac) або **Cloud GPU** (той самий
     Canary на GPU в EU, ~2 хв на годину запису). Апка сама рекомендує варіант під твій Mac
     (бейдж «Recommended for this Mac»): Pro/Max/Ultra з 16+ ГБ → Local, базові M-чипи,
     Intel або <16 ГБ → Cloud GPU. Переключити можна будь-коли в Settings;
   - **завантажити модель** (для Local) — цей крок **можна пропустити** і зробити пізніше
     в Settings → System Readiness;
   - **сховище записів**: Google Drive (рекомендовано) або локально;
   - **Claude Code** — кнопка «Authorize Claude» установить і залогінить його сама; якщо
     бінар уже є, апка його знайде.
3. Встанови розширення [з Chrome Web Store](https://chromewebstore.google.com/detail/sumeeting/olciponfpbfpaohpjclonfebcmaeeghd).

### Якщо macOS каже «Apple could not verify "SuMeeting" is free of malware»

Це наслідок бага у версіях **≤0.5.2**: апка тоді сама псувала власний підпис під час
роботи, а заблокована апка не може оновитися. Разово виконай у Terminal:

```
find /Applications/SuMeeting.app -name __pycache__ -type d -exec rm -rf {} +
```

або просто перевстанови апку зі свіжого `SuMeeting.dmg` (записи не зникнуть — вони
лежать окремо в `~/Library/Application Support/SuMeeting`). З 0.5.3 проблема виправлена
і більше не повторюється.

### Якщо Google при вході показує «Google hasn't verified this app»

Апка запитує доступ до Google Calendar (лише читання подій — щоб узяти список учасників
мітингу), і Google показує це попередження, поки триває верифікація застосунку. Натисни
**Advanced → Go to SuMeeting** і дай дозволи — це безпечно, дані календаря нікуди, крім
твого Mac, не йдуть (див. [Privacy Policy](https://sumeeting.aura-shield.app/privacy.html)).

## Використання

1. Запусти **SuMeeting.app** (він тримає локальний бекенд).
2. Зайди в дзвінок Google Meet.
3. **Вкажи своє ім'я в розширенні** — коли говориш ти, Google Meet тобі цього не
   показує, тож із указаним ім'ям транскрипції набагато легше правильно розділити мовців.
4. Натисни **⌘⇧E** або іконку розширення → **Start recording** (дай дозвіл на мікрофон
   при першому разі). Мікрофон береться той самий, що зараз у Meet.
5. Після дзвінка натисни **Stop** — або просто **вийди з дзвінка / закрий вкладку**, запис
   завершиться сам. Запис піде на обробку, транскрипція і summary з'являться в
   застосунку SuMeeting.
