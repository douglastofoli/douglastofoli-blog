---
title: "Using Nix for Productivity"
date: 2023-03-02T14:30:10-03:00
draft: false
tags: [nix]
comments: true
---

I love automations, and set up environments to development is very stressfull. Since I've been using Nix I've been had less work to configure my packages and my configurations.

And make your environment productivy is really easy. In some steps.

You need to have the package manager Nix installed on your system. Also need direnv, for integration, that enables automations.

Install Nix in whatever Linux distribution is simple, just run the installer:
```shell
sh <(curl -L https://nixos.org/nix/install) --daemon
```

To install direnv you can use the package manager for your Linux distribution, like apt or pacman:
```
sudo apt install direnv
```

_or_

```
sudo pacman -S direnv
```

Check {{< external-link url="https://direnv.net/docs/installation.html" text="documentation" >}} for more options installation.

To finish the setup, create the Nix config to enable Flakes. Just run in terminal:
```
mkdir -p ~/.config/nix
echo "experimental-features = nix-command flakes" >> ~/.config/nix/nix.conf
```

And restart the nix daemon:
```
sudo systemctl restart nix-daemon
```

{{< break >}}

And that is all! You now can run Nix and build flakes for make your dev environment more productivy.

{{< break >}}

Fonts: {{< external-link url="https://nixos.org/download.html" text="NixOs" >}}, {{< external-link url="https://nixos.wiki/wiki/Flakes" text="Flakes" >}}, {{< external-link url="https://direnv.net/docs/installation.html" text="Direnv Installation" >}}
