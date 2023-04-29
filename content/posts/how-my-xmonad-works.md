---
title: "How My XMonad Works"
date: 2023-04-29T11:27:00-03:00
draft: false
---

# XMonad Configuration

This is my personal configuration file for [XMonad](https://xmonad.org/), a tiling window manager for X11. This configuration is highly customized and may not suit your needs out of the box, but you are welcome to use it as a starting point for your own configuration.

## Table of Contents

- [Dependencies](#dependencies)
- [Installation](#installation)
- [Customization](#customization)
  - [Variables](#variables)
  - [Navigation](#navigation)
  - [Workspaces](#workspaces)
  - [Startup](#startup)
- [Layout](#layout)
- [Keybindings](#keybindings)

## Dependencies

Before you can use this configuration, you will need to install the following dependencies:

- [XMonad](https://xmonad.org/)
- [xmonad-contrib](https://hackage.haskell.org/package/xmonad-contrib)
- [xmobar](https://github.com/jaor/xmobar)
- [rofi](https://github.com/davatorium/rofi)

## Installation

To install this configuration, follow these steps:

1. Clone my repository:

```
git clone https://github.com/douglastofoli/nix-configs
```

2. Copy the configuration files to your home directory:

```
cd nix-configs
cp modules/desktop/xmonad/xmonad.hs ~/.config/xmonad/
cp modules/desktop/xmonad/xmobar/xmobarrc ~/.config/xmobar/
```

3. Restart XMonad:

```
xmonad --restart
```

## Customization

This configuration is highly customizable. To modify the behavior of XMonad, edit the `xmonad.hs` file in your `~/.config/xmonad/` directory. To modify the behavior of xmobar, edit the `xmobarrc` file in your `~/.config/xmobar/` directory.

### Variables

This configuration uses several variables to control various aspects of XMonad's behavior, such as the default terminal emulator, the mod key, and the font used by xmobar. These variables are defined at the top of the `xmonad.hs` file and can be modified to suit your preferences.

### Navigation

This configuration includes several keybindings for navigating between windows and workspaces. Some of the keybindings that are defined in this configuration include:

- `mod + j/k`: move focus to the next/previous window
- `mod + h/l`: resize the master window
- `mod + [1-9]`: switch to the specified workspace
- `mod + shift + [1-9]`: move the current window to the specified workspace

To see a full list of keybindings, see the `xmonad.hs` file.

### Workspaces

This configuration uses dynamic workspaces. By default, this configuration creates 9 workspaces, numbered 1-9.

To switch between workspaces, use the following keybindings:

- `mod + [1-9]`: switch to the specified workspace
- `mod + shift + [1-9]`: move the current window to the specified workspace

### Startup

This configuration includes a `startupHook` function that is run when XMonad starts up. This function can be used to perform various tasks, such as starting applications or setting the wallpaper.

To modify the startupHook, see the `xmonad.hs` file.

## Layout

This configuration uses several layouts for arranging windows, including:

### Tall

This is the default layout. Windows are arranged in a tiled pattern, with the master window taking up the largest portion of the screen. This layout is defined as follows:

```haskell
tall =
  renamed [Replace "tall"] $
    limitWindows 5 $
      smartBorders $
        windowNavigation $
          addTabs shrinkText myTabTheme $
            subLayout [] (smartBorders Simplest) $
              mySpacing 8 $
                ResizableTall 1 (3 / 100) (1 / 2) []
```

### Monocle

This layout makes the current window take up the entire screen. It is defined as follows:

```haskell
monocle =
  renamed [Replace "monocle"] $
    smartBorders $
      windowNavigation $
        addTabs shrinkText myTabTheme $
          subLayout [] (smartBorders Simplest) $
            Full
```

### Floats

This layout allows windows to be placed freely on the screen. It is defined as follows:

```haskell
floats =
  renamed [Replace "floats"] $
    smartBorders $
      simplestFloat
```

### Grid

This layout arranges windows in a grid pattern. It is defined as follows:

```haskell
grid =
  renamed [Replace "grid"] $
    limitWindows 9 $
      smartBorders $
        windowNavigation $
          addTabs shrinkText myTabTheme $
            subLayout [] (smartBorders Simplest) $
              mySpacing 8 $
                mkToggle (single MIRROR) $
                  Grid (16 / 10)
```

### Spirals

This layout arranges windows in a spiral pattern. It is defined as follows:

```haskell
spirals =
  renamed [Replace "spirals"] $
    limitWindows 9 $
      smartBorders $
        windowNavigation $
          addTabs shrinkText myTabTheme $
            subLayout [] (smartBorders Simplest) $
              mySpacing' 8 $
                spiral (6 / 7)
```

### ThreeCol

This layout arranges windows in three columns. It is defined as follows:

```haskell
threeCol =
  renamed [Replace "threeCol"] $
    limitWindows 7 $
      smartBorders $
        windowNavigation $
          addTabs shrinkText myTabTheme $
            subLayout [] (smartBorders Simplest) $
              ThreeCol 1 (3 / 100) (1 / 2)
```

### ThreeRow

This layout arranges windows in three rows. It is defined as follows:

```haskell
threeRow =
  renamed [Replace "threeRow"] $
    limitWindows 7 $
      smartBorders $
        windowNavigation $
          addTabs shrinkText myTabTheme $
            subLayout [] (smartBorders Simplest) $
              Mirror $
                ThreeCol 1 (3 / 100) (1 / 2)
```

### Tabs

This layout arranges windows in tabs. It is defined as follows:

```haskell
tabs =
  renamed [Replace "tabs"] $
    tabbed shrinkText myTabTheme
```

### TallAccordion

This layout arranges windows in a tall accordion pattern. It is defined as follows:

```haskell
tallAccordion =
  renamed [Replace "tallAccordion"] $
    Accordion
```

### WideAccordion

This layout arranges windows in a wide accordion pattern. It is defined as follows:

```haskell
wideAccordion =
  renamed [Replace "wideAccordion"] $
    Mirror Accordion
```

The `Mirror` modifier flips the layout horizontally, so that the wider pane is on the left, and the narrower panes are on the right. This layout is useful when you have a wide-screen monitor and you want to view multiple windows side by side.

You can switch between layouts using the following keybindings:

- `mod + tab`: cycle through the available layouts

You can customize the appearance and behavior of `wideAccordion` layout by modifying the layout hook and other related settings in your XMonad configuration.

## Keybindings

XMonad is controlled entirely by keybindings. The default keybindings are defined in the `config` variable in your XMonad configuration file (`~/.xmonad/xmonad.hs` by default). You can customize these keybindings or define new ones to suit your workflow.

Here are some of the default keybindings:

- `mod + shift + q`: Quit XMonad.
- `mod + d`: Launch `rofi` to open programs.
- `mod + shift + c`: Close the focused window.
- `mod + tab`: Cycle through the available layouts.
- `mod + j`: Focus the next window.
- `mod + k`: Focus the previous window.
- `mod + h`: Shrink the master window.
- `mod + l`: Expand the master window.
- `mod + shift + j`: Swap the focused window with the next window.
- `mod + shift + k`: Swap the focused window with the previous window.
- `mod + t`: Push the floating window back into tiling mode.
- `mod + shift + t`: Push all floating windows back into tiling mode.
- `mod + space`: Toggle full screen mode for the focused window.

Note that `mod` refers to the modifier key, which is typically the `Alt` key or the `Windows` key. You can change the modifier key by modifying the `modMask` variable in your XMonad configuration file.

## Final words

In conclusion, XMonad is an incredibly flexible and powerful tiling window manager that allows you to create a desktop environment that fits your specific needs and workflow. By tweaking its configuration file, you can customize everything from your keybindings to your workspaces, layouts, and status bars. So if you're looking for a lightweight and highly customizable window manager for your Linux desktop, give XMonad a try – you might just be surprised at how much you can accomplish with it!
