# TriggerOS — пост-анонс (русский)

> Готово к вставке. Под каждую площадку убери лишнее. Всегда прикладывай ссылку и скриншот.
> Репозиторий: https://github.com/Ttriggeredbot/TriggerOS

---

## Короткий заголовок (4PDA / VK / Telegram)

**TriggerOS — Android 15 + настоящие Linux-программы в окнах на Nintendo Switch OLED (с Vulkan через NVK)**

---

## Тело поста (4PDA / Habr / форумы)

**TriggerOS** — неофициальная система для **Nintendo Switch OLED (Mariko / Tegra X1+)** на базе LineageOS 22.2 (switchroot). Рядом работают **Android 15 и полноценная Ubuntu 26.10**: графические Linux-программы открываются **обычными окнами Android**, в списке «Недавние», как в ChromeOS. Без перезагрузки и без второго рабочего стола.

Чем отличается от существующих портов Linux/Android на Switch:

- **Linux-программы как окна Android** — свой Wayland-композитор (`trigwm`), каждое окно Linux — отдельная задача Android, кадр отдаётся композитору Android без копирования.
- **Vulkan на GPU Switch через Mesa NVK** — свой модуль ядра (`trigdrm`) открывает GPU Tegra X1 немодифицированному Mesa NVK. `vkcube` и `vkmark` работают прямо в окне (скриншот ниже). Это дорога к **DXVK / Proton / Steam**.
- **Свой интерфейс** — главный экран, меню программ, «Недавние», значки, анимация загрузки, терминал в стиле «16 бит», установщик приложений в один тап (браузер, офис, GIMP, Krita, mpv …).
- **Своя сборка ядра L4T 4.9** — zram с выгрузкой, гейтинг питания GPU, правки дисплея.

**Чисто по лицензиям:** никакой прошивки, ключей и марок Nintendo; изменения ядра (GPL) опубликованы; благодарности switchroot и LineageOS.

**Статус:** публичная бета (0.7.x). Установка через hekate + recovery (`adb sideload`), установка на eMMC тоже есть. **Нужен модчип** — на Mariko нет программного RCM-эксплойта, об этом честно предупреждаем.

Скриншот — куб Vulkan (NVK) в окне на самой Switch:
`assets/vulkan.png`

Репозиторий, релизы и инструкция: https://github.com/Ttriggeredbot/TriggerOS

Отзывы и баги — в Issues / Discussions.

---

## Однострочник для Discord / чата

TriggerOS: Android 15 + Ubuntu в окнах на Switch OLED, теперь с Vulkan через NVK (vkcube/vkmark работают в окне). Публичная бета, нужен модчип. https://github.com/Ttriggeredbot/TriggerOS
