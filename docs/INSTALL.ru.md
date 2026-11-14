# Установка TriggerOS

[English version](INSTALL.en.md)

> ⚠️ Вы всё делаете на свой риск. Разметка SD-карты **стирает её полностью**. Перед началом сохраните всё нужное с карты
> и сделайте резервную копию eMMC в hekate (Tools → Backup eMMC → eMMC BOOT0 & BOOT1 и eMMC RAW GPP).

## Что нужно
- Nintendo Switch **OLED** с модчипом и загрузчиком **hekate** (свежая версия, 6.x).
  Протестировано на OLED; на других моделях пока не проверялось.
- **microSD от 64 ГБ** (лучше 128 ГБ, класс A1/A2). Под Android отдаётся от 32 ГБ, рекомендуем 48 ГБ и больше —
  внутри живёт ещё и Ubuntu.
- Компьютер с **ADB** ([Android Platform Tools](https://developer.android.com/tools/releases/platform-tools)) и USB-C кабель.

## Файлы релиза
Скачайте со страницы [Releases](https://github.com/Ttriggeredbot/TriggerOS/releases/latest):

| Файл | Что это |
|---|---|
| `TriggerOS-0.7-20261114-nx_tab.zip` | сама система (ставится через recovery, **не распаковывать**) |
| `TriggerOS-0.7-boot-sd.zip` | загрузочный комплект для SD-карты (распаковать в корень карты) |
| `SHA256SUMS.txt` | контрольные суммы |

## Установка на SD-карту

### 1. Разметка карты
1. Загрузите hekate, вставьте карту.
2. **Tools → Partition SD Card.**
3. Ползунком **Android (Dynamic)** задайте размер (от 32 ГБ, лучше 48+). Остальное останется под FAT32 (файлы hekate).
   Раздел **Linux (L4T)** не нужен — Ubuntu уже внутри TriggerOS.
4. **Next Step → Start.** Дождитесь окончания. hekate сам сохранит и вернёт файлы с карты (до 1 ГБ).

### 2. Загрузочный комплект
1. В hekate: **Tools → USB Tools → SD Card** — карта появится на компьютере как флешка.
2. Распакуйте `TriggerOS-0.7-boot-sd.zip` **в корень карты** (папки `bootloader` и `switchroot` сольются с существующими).
3. Безопасно извлеките карту на компьютере и закройте режим USB в hekate.

### 3. Прошивка разделов загрузки
1. В hekate: **Tools → Partition SD Card → Flash Android.**
2. hekate запишет ядро, recovery и dtb из папки `switchroot/install`. Когда спросит про перезагрузку в recovery — согласитесь.
   Если не спросил — см. следующий шаг.

### 4. Вход в recovery
**Зажмите VOL+** и выберите в hekate **More Configs → TriggerOS**. Держите VOL+, пока не появится меню recovery.

### 5. Установка системы
1. В recovery: **Factory reset → Format data/factory reset** (только при первой установке).
2. **Apply update → Apply from ADB.**
3. Подключите консоль к компьютеру кабелем и выполните:
   ```
   adb sideload TriggerOS-0.7-20261114-nx_tab.zip
   ```
   Счётчик может остановиться на ~47% и написать `Total xfer: 1.00x` — это нормально.
4. Когда recovery сообщит об успешной установке — **Reboot system now**.

Первая загрузка идёт несколько минут. Ubuntu распаковывается при первом запуске Linux-программы (~10 секунд).

### Как потом запускать
hekate → **More Configs → TriggerOS** (можно поставить в автозагрузку в настройках hekate).

## Обновление
VOL+ при запуске → recovery → **Apply from ADB** → `adb sideload <новый zip>` → Reboot.
**Format data при обновлении не нужен** — программы и файлы сохраняются.

## Установка на внутреннюю память (eMMC)
TriggerOS умеет работать и с внутренней памяти — так её ставили мы. Это быстрее SD, но сложнее и рискованнее:
нужно освободить место на eMMC и создать на ней Android-разделы (`boot`, `recovery`, `dtb`, `misc`, `cache`,
`super`, `userdata`), **не трогая** служебные разделы Nintendo (PRODINFO и др.). Делайте это только если понимаете,
что такое GPT, и только с полной резервной копией eMMC.

Отличия от установки на SD:
- в файле `bootloader/ini/triggeros.ini` на SD добавьте строку `emmc=1`;
- карта всё равно нужна — на ней лежат hekate и `switchroot/android/*` для загрузки;
- встроенный менеджер eMMC в hekate может зависнуть на консолях без раздела HOS USER — в таком случае
  выключите консоль (зажать кнопку питания 15 с), он ничего не успевает записать.

Подробная инструкция для eMMC появится в следующих версиях.

## Если что-то пошло не так
- **Консоль не грузится дальше логотипа** — зайдите в recovery (VOL+) и повторите `adb sideload`.
- **Не видно устройства в `adb`** — на Linux нужно udev-правило для USB ID `057e`, на Windows — драйвер Google USB.
- Вернуть Horizon просто: TriggerOS живёт на своих разделах, загрузка HOS из hekate работает как раньше.

Вопросы и ошибки — в [Issues](https://github.com/Ttriggeredbot/TriggerOS/issues).
