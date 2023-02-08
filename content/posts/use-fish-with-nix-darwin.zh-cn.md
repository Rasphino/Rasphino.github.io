+++ 
draft = false
date = 2023-02-08T12:00:00+08:00
title = "使用 nix-darwin 为 macOS 启用 fish"
description = ""
slug = ""
tags = ["Nix", "nix-darwin", "fish"]
categories = ["教程"]
externalLink = ""
series = []
+++

在 nix-darwin 的配置文件（例如你的`configuration.nix`）中添加：
```nix
programs.fish.enable = true;
environment.shells = [ pkgs.bashInteractive pkgs.zsh pkgs.fish ];

users.users.<name> = {
    name = "<name>";
    home = "/Users/<name>";
    shell = pkgs.fish;
};
```

参见：[nix-darwin issue](https://github.com/LnL7/nix-darwin/issues/515)
