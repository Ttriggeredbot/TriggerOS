# TriggerOS — announcement post (English)

> Copy–paste ready. Trim the intro per platform. Always link the repo and a screenshot.
> Repo: https://github.com/Ttriggeredbot/TriggerOS

---

## Short version (Reddit title / HN "Show HN")

**TriggerOS — Android 15 + real Linux apps in windows on the Nintendo Switch OLED (with Vulkan via NVK)**

---

## Body (Reddit / GBATemp / forums)

**TriggerOS** is an unofficial OS for the **Nintendo Switch OLED (Mariko / Tegra X1+)**, built on LineageOS 22.2 (switchroot). It runs **Android 15 and a full Ubuntu 26.10 side by side** — Linux GUI programs open as **ordinary Android windows**, in the Recents list, next to Android apps. No reboot, no separate desktop, ChromeOS-style.

What makes it different from existing Switch Linux/Android ports:

- **Linux apps as Android windows** — our own Wayland compositor (`trigwm`), each Linux window is its own Android task with zero-copy into the Android compositor.
- **Vulkan on the Switch GPU via Mesa NVK** — a custom kernel DRM shim (`trigdrm`) exposes the Tegra X1 GPU to unmodified Mesa NVK. `vkcube` and `vkmark` run inside a window (screenshot below). This is the path to **DXVK / Proton / Steam** later.
- **Own UI** — home screen, app drawer, Recents, icons, boot animation, a 16-bit style terminal, a one-tap app installer (browser, office, GIMP, Krita, mpv, …).
- **Custom L4T 4.9 kernel** — zram writeback, GPU power gating, display tweaks.

**License-clean:** no Nintendo firmware, keys or marks; GPL kernel changes published; credits to switchroot and LineageOS.

**Status:** public beta (0.7.x). Install via hekate + recovery (`adb sideload`); eMMC install also supported. Requires a modchip (Mariko has no software RCM exploit — be honest about this with users).

Screenshot — Vulkan (NVK) cube running in a window on the Switch:
`assets/vulkan.png`

Repo, releases and install guide: https://github.com/Ttriggeredbot/TriggerOS

Feedback and bug reports welcome in Issues / Discussions.

---

## One-liner for Discord / chat

TriggerOS: Android 15 + Ubuntu in windows on Switch OLED, now with Vulkan via NVK (vkcube/vkmark run in a window). Public beta, modchip required. https://github.com/Ttriggeredbot/TriggerOS
