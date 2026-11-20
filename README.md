# tinted-herdr

A [Tinted Theming] template for the [Herdr] desktop app. It renders every
[Base16] and [Base24] scheme as a Herdr theme file, and [Tinty] can apply those
themes alongside the rest of your tools.

## Installation

### With Tinty

This repository is private, so installing it requires read access and a GitHub
SSH key. Tinty clones items with your own `git` binary, which uses your SSH key
in the same way as a manual `git clone`.

Add the following to `~/.config/tinted-theming/tinty/config.toml`:

```toml
[[items]]
name = "tinted-herdr"
path = "https://github.com/pardom/tinted-herdr"
themes-dir = "themes"
supported-systems = ["base16", "base24"]
hook = "mkdir -p \"$HOME/.config/herdr-app/themes\" && cp -f \"$TINTY_THEME_FILE_PATH\" \"$HOME/.config/herdr-app/themes/tinted.json\""
```

Then run `tinty sync` and apply a scheme:

```sh
tinty sync
tinty apply base16-rose-pine-moon
```

The hook always writes to the same file, `themes/tinted.json`. Select the
`tinted` theme once in Herdr's settings. After that, Herdr reloads the file
whenever Tinty overwrites it, so a new scheme appears without a restart or a
second selection.

### Manually

Copy a file from `themes/` into `~/.config/herdr-app/themes/` and select it in
Herdr's settings. The theme takes its name from the filename.

[Tinted Theming]: https://github.com/tinted-theming/home
[Herdr]: https://herdr.dev
[Tinty]: https://github.com/tinted-theming/tinty
[Base16]: https://github.com/tinted-theming/home/blob/main/styling.md
[Base24]: https://github.com/tinted-theming/base24/blob/master/styling.md
