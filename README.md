<h1 align="center">ansi.mq</h1>

ANSI terminal escape code utilities implemented as an [mq](https://github.com/harehare/mq) module.

## Features

- Text styles: bold, dim, italic, underline, strikethrough
- Standard foreground colors (8 colors + bright variants)
- Background colors (8 colors)
- 24-bit RGB foreground and background colors
- Strip ANSI codes from strings
- Compute visible length (excluding escape codes)

## Installation

Copy `ansi.mq` to your mq module directory:

```sh
cp ansi.mq ~/.mq/
```

## Usage

```sh
mq -I raw 'import "ansi" | ansi::ansi_green("✓ OK")' input.md
```

## API

### Styles

| Function | Effect |
|---|---|
| `ansi_bold(s)` | **Bold** |
| `ansi_dim(s)` | Dim / faint |
| `ansi_italic(s)` | *Italic* |
| `ansi_underline(s)` | Underline |
| `ansi_strikethrough(s)` | ~~Strikethrough~~ |

### Foreground Colors

| Function | Color |
|---|---|
| `ansi_red(s)` | Red |
| `ansi_green(s)` | Green |
| `ansi_yellow(s)` | Yellow |
| `ansi_blue(s)` | Blue |
| `ansi_magenta(s)` | Magenta |
| `ansi_cyan(s)` | Cyan |
| `ansi_white(s)` | White |
| `ansi_bright_red(s)` | Bright red |
| `ansi_bright_green(s)` | Bright green |
| `ansi_bright_yellow(s)` | Bright yellow |
| `ansi_bright_blue(s)` | Bright blue |
| `ansi_bright_magenta(s)` | Bright magenta |
| `ansi_bright_cyan(s)` | Bright cyan |
| `ansi_bright_white(s)` | Bright white |

### Background Colors

| Function | Color |
|---|---|
| `ansi_bg_red(s)` | Red background |
| `ansi_bg_green(s)` | Green background |
| `ansi_bg_yellow(s)` | Yellow background |
| `ansi_bg_blue(s)` | Blue background |
| `ansi_bg_magenta(s)` | Magenta background |
| `ansi_bg_cyan(s)` | Cyan background |
| `ansi_bg_white(s)` | White background |

### 24-bit Color

| Function | Description |
|---|---|
| `ansi_rgb(s, r, g, b)` | 24-bit foreground (0–255 per channel) |
| `ansi_bg_rgb(s, r, g, b)` | 24-bit background (0–255 per channel) |

### Utilities

| Function | Description |
|---|---|
| `ansi_strip(s)` | Remove all ANSI escape codes |
| `ansi_len(s)` | Visible length (after stripping codes) |

## Example

```sh
# Colorize mq test output labels
mq '
  import "ansi"
  | if (contains(., "PASS")):
      ansi::ansi_green(.)
    else:
      ansi::ansi_red(.)
' results.md

# Print a header with bold cyan text
mq -I raw '"Report" | import "ansi" | ansi::ansi_bold(ansi::ansi_cyan(.))' /dev/null
```

## Compatibility

Requires [mq](https://github.com/harehare/mq) v0.5 or later.
Terminal support depends on the environment; most modern terminals support ANSI codes.

## License

MIT
