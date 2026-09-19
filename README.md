# pi-catppuccin-theme

Catppuccin themes for the [pi coding agent](https://pi.dev):

| theme | flavor | background | when |
|---|---|---|---|
| `catppuccin-frappe` | Frappé | `#303446` (dark) | 终端是深色时 |
| `catppuccin-latte` | Latte | `#eff1f5` (light) | 终端是浅色时 |

两个主题可以配成一对，让 pi 跟随终端明暗自动切换：

```json
{ "theme": "catppuccin-latte/catppuccin-frappe" }
```

**只包含主题。** 包里没有 `extensions/`、`skills/`、`prompts/`，`package.json` 的 `pi` 清单里也只声明了 `themes` —— 因此安装和使用过程中**不会占用任何 prompt / context token**（主题是纯渲染层，从不发给模型）。

## 安装

```bash
# git（推荐，便于多机同步）
pi install git:github.com/<you>/pi-catppuccin-theme
pi install git:github.com/<you>/pi-catppuccin-theme@v1.0.0   # 固定版本

# npm
pi install npm:pi-catppuccin-theme

# 本地目录 / U 盘 / 解包的 tarball
pi install /absolute/path/to/pi-catppuccin-theme

# 只试用一次，不写进配置
pi -e git:github.com/<you>/pi-catppuccin-theme
```

然后在 pi 里 `/settings` → Theme 选 `catppuccin-latte/catppuccin-frappe`（或只选单个）。

检查装了什么、加载了哪些资源（应当只有 Themes 一栏）：

```bash
pi list
pi config
```

## 速查：关键 token

| token | Frappé（暗） | Latte（亮） | 用途 |
|---|---|---|---|
| `mdCode` | `#CA9EE6` | `#8839EF` | 行内代码 |
| `syntaxKeyword` | `#CA9EE6` | `#8839EF` | 代码关键字 |
| `accent` | `#CA9EE6` | `#8839EF` | logo / 选中行 / 光标 |
| `syntaxFunction` | `#8CAAEE` | `#1E66F5` | 函数名 |
| `syntaxVariable` | `#F2D5CF` | `#DC8A78` | 变量 |
| `syntaxString` | `#A6D189` | `#40A02B` | 字符串 |
| `syntaxNumber` | `#EF9F76` | `#FE640B` | 数字 |
| `syntaxType` | `#E5C890` | `#DF8E1D` | 类型 |
| `syntaxOperator` | `#99D1DB` | `#04A5E5` | 运算符 |
| `syntaxComment` | `#838BA7` | `#8C8FA1` | 注释 |
| `mdHeading` | `#E5C890` | `#DF8E1D` | 标题 |
| `mdLink` | `#8CAAEE` | `#1E66F5` | 链接 |
| `text` / `muted` / `dim` | `#C6D0F5` / `#B5BFE2` / `#949CBB` | `#4C4F69` / `#5C5F77` / `#7C7F93` | 正文 / 次级 / 弱化 |
| `border` / `borderMuted` | `#626880` / `#51576D` | `#ACB0BE` / `#BCC0CC` | 边框 |
| `userMessageBg` / `toolSuccessBg` / `toolErrorBg` | `#292C3C` / `#2C3A32` / `#3A2A31` | `#E6E9EF` / `#E3F1DF` / `#F7E3E3` | 背景 |

色值取自官方 [catppuccin/palette](https://github.com/catppuccin/palette) 的 `palette.json`。

## 自定义

主题就是普通 JSON。装好后想微调，两个办法：

1. 直接改本仓库的 `themes/*.json`，然后 `pi update` / 重新 `pi install`。
2. 复制到 `~/.pi/agent/themes/` 自己改 —— 该目录下的同名主题优先级更高，
   而且**编辑当前生效的那个文件会热重载**，即改即见。

注意：文件里的 `name` 字段必须与文件名一致，且不能包含 `/`（斜杠是 pi 用来分隔 `亮/暗` 配对的）。

## 配套：终端底色

pi 只能给自己的界面区域上色，页面底色由终端决定。想让观感统一，把终端也换成 Catppuccin Frappé
（kitty / iTerm2 / WezTerm / Windows Terminal 官方都有主题文件）。

## License

MIT，见 [LICENSE](LICENSE)。Catppuccin 调色板本身同样以 MIT 发布。
