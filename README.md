<p align="center">
  <img src="assets/logo.png" width="120" alt="TriggerOS">
</p>

<h1 align="center">TriggerOS</h1>

<p align="center">
  <b>Android 15 + настоящий Linux на одном экране</b><br>
  <b>Android 15 + real Linux on one screen</b>
</p>

<p align="center">
  <a href="https://github.com/Ttriggeredbot/TriggerOS/releases/latest"><img src="https://img.shields.io/github/v/release/Ttriggeredbot/TriggerOS?style=for-the-badge&color=B13FB3&label=release" alt="release"></a>
  <img src="https://img.shields.io/badge/Android-15-E76C2E?style=for-the-badge" alt="Android 15">
  <img src="https://img.shields.io/badge/Linux-Ubuntu%2026.10-FFB27A?style=for-the-badge" alt="Ubuntu">
  <img src="https://img.shields.io/badge/device-Tegra%20X1%20(OLED)-3C2D3A?style=for-the-badge" alt="device">
</p>

<p align="center">
  <a href="#русский">Русский</a> · <a href="#english">English</a>
</p>

<p align="center">
  <img src="assets/home.png" width="49%" alt="Home">
  <img src="assets/apps.png" width="49%" alt="Apps">
</p>

---

## Русский

**TriggerOS** — неофициальная система для консоли Nintendo Switch (модель OLED), основанная на LineageOS 22.2 (switchroot).
Скорость и приложения Android, а рядом — полноценная Ubuntu: Linux-программы открываются в обычных окнах Android,
как в ChromeOS. Без перезагрузки и без второго рабочего стола.

### Что внутри
- **Свой интерфейс:** главный экран, меню программ и «Недавние» в палитре TriggerOS, свои значки, своя анимация загрузки.
- **Linux-программы в окнах:** собственный Wayland-композитор `trigwm`; окна Linux живут в списке задач рядом с Android.
- **Tterminal:** терминал в стиле «16 бит» (пиксельный шрифт Terminus, палитра TriggerOS); строка ввода всегда над клавиатурой.
- **Установщик:** выбираешь пальцем браузер, офис, GIMP, Krita, mpv и другие — и они ставятся сами и появляются в меню.
- **Ядро:** своя сборка L4T 4.9 — zram с выгрузкой, планировщик питания GPU, правки дисплея.
- **«Консоль»:** настройки джойконов и консоли на языке системы (RU/EN).

### Установка
📖 **[Инструкция по установке (RU)](docs/INSTALL.ru.md)**

Коротко: hekate → разметить SD-карту под Android → скопировать загрузочный комплект → прошить через recovery (`adb sideload`).
Установка на внутреннюю память (eMMC) тоже возможна — см. раздел в инструкции.

### Статус
`0.7.1` — первый публичный релиз. Это бета: возможны ошибки — пишите в [Issues](https://github.com/Ttriggeredbot/TriggerOS/issues).

---

## English

**TriggerOS** is an unofficial OS for the Nintendo Switch (OLED model) based on LineageOS 22.2 (switchroot).
Android speed and apps, plus a full Ubuntu next to it: Linux programs open in regular Android windows,
like on ChromeOS. No reboot, no second desktop.

### What's inside
- **Own interface:** home screen, app drawer and Recents in the TriggerOS palette, own icons and boot animation.
- **Linux apps in windows:** our own Wayland compositor `trigwm`; Linux windows sit in the task list next to Android apps.
- **Tterminal:** a "16-bit" terminal (Terminus pixel font, TriggerOS palette); the input line always stays above the keyboard.
- **Installer:** pick a browser, office suite, GIMP, Krita, mpv and more with your finger — they install and show up in the menu.
- **Kernel:** our own L4T 4.9 build — zram writeback, GPU power gating, display fixes.
- **Console app:** Joy-Con and device settings in the system language (EN/RU).

### Installation
📖 **[Installation guide (EN)](docs/INSTALL.en.md)**

In short: hekate → partition the SD card for Android → copy the boot kit → flash via recovery (`adb sideload`).
Installing to internal storage (eMMC) is also possible — see the guide.

### Status
`0.7.1` is the first public release. It is a beta: bugs are possible — please report them in [Issues](https://github.com/Ttriggeredbot/TriggerOS/issues).

---

<sub>
TriggerOS is not affiliated with, endorsed or sponsored by Nintendo, Google, Canonical, NVIDIA or the LineageOS project.
"Nintendo Switch" is a trademark of Nintendo; it is used here only to describe hardware compatibility.
The release contains no Nintendo firmware, keys or copyrighted Nintendo content.
See <a href="AUTHORS.md">AUTHORS.md</a> for credits and <a href="NOTICE.md">NOTICE.md</a> for licenses and sources.
</sub>
