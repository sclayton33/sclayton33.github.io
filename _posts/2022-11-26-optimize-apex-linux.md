---
layout: post
title: Optimizing Apex Legends for playing on Linux systems
date: 2022-11-26 21:39:00 -11:00
description: short guide outlining some methods to improve the gameplay experience on Linux
tags: linux gaming
categories: computer
---

With the progress made largely by Valve and other developers on the compatability layer [Proton](https://github.com/ValveSoftware/Proton), it is now possible to play many games on Linux that historically have been unplayable. With their push for some anti-cheat support (namely Easy Anti-Cheat and Battleye) leading up to the Steam Deck release, many games with anti-cheat are now also playable. Apex Legends being one of them.

This brief article will highlight some things you can try to optimize your gameplay experience on Linux.

---

## Steam tweaks

1.) Set launch options

Right-click on Apex Legends in Steam > properties > general > launch options.

```
dxvk_hud=compiler gamemoderun %command% -novid -high +fps_max 96
```

Descriptions of commands:

- `dxvk_hud=compiler`
  - Only displays when shaders are being compiled
- [`gamemoderun`](https://github.com/FeralInteractive/gamemode)
  - Produces on-demand performance boosts for games.
- `-novid`
  - Not a performance benefit perse, but saves you a few seconds each launch by not watching the splash screen.
- `-high`
  - Sets high process priority for the game. This may be redundant as gamemoderun should increase priority.
- `+fps_max 96`

  - Set this to your monitors refresh rate minus 4, e.g. if it's 100, you would put 96. This should help prevent tearing and stutter.

  2.) Proton experimental

Switching to the experimental branch may offer some performance improvements. You can also use the _bleeding-edge_ branch, which I do personally. To switch to it, go to your steam library > set filter to tools > find Proton Experimental in the list > right-click > properties > Betas > bleeding-edge.

It's important to note that you **should not use bleeding-edge for every game** and back up your game prefixes before using it. I won't explain how to do that here though.

---

## Desktop Environment

Unlike on Windows, you have many options for different desktop environments on Linux. Your choice may impact how well games perform and how responsive they feel.

After trying out many different combinations, here is what I feel to be the best:

- KDE Plasma X11
  - These settings are not relevant if you are using Wayland.
- Compositing turned off
  - `alt + shift + F12` will enable/disable it.
  - Check if it's disabled by running this from command line, false means it is disabled.
    - `qdbus org.kde.KWin /Compositor org.kde.kwin.Compositing.active`

Hopefully this helps your games!
