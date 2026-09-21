# funny-characters · 怪字输入法

随便敲，认真乱写。

一个会把你输入的文字随机替换成生僻字符的网页小工具。敲几下键盘，再复制给同学猜猜看。

![界面预览](preview.png)

## 直接使用

1. 下载本仓库，双击 `index.html`，用浏览器打开。
2. 点击输入框，随便输入文字。英文按键即时转换；中文输入法完成选字后转换。
3. 点击 **复制全部**，粘贴到聊天里。

不用安装依赖，不需要服务器，断网也能使用。保存或转发单独一个 `index.html` 即可。

## 能做什么

- 从 **514 个字符**中随机选择：133 个生僻汉字、169 个楔形文字、96 个古埃及象形文字、116 个炼金术符号。
- 每输入一个 Unicode 码点，随机生成一个字符；避免连续生成同一个字符。
- 保留空格和换行，支持粘贴、选区替换、光标插入和退格删除。
- 支持 `⌘Z / Ctrl+Z` 撤销、`⌘⇧Z / Ctrl+Shift+Z` 重做，以及一键清空。
- 一键复制；浏览器不允许自动复制时，保留选中的文本供手动复制。
- 页面内嵌所需字体，不使用 CDN，不上传输入内容，不写入本地存储。

这是只在网页输入框内生效的娱乐工具，没有安装系统输入法，也不提供古文字翻译。复制出去的是 Unicode 文本；接收方的设备若缺少对应字体，可能显示方框。

## 源代码

所有程序代码都在 `index.html`：

- `<style>`：页面样式和内嵌的 WOFF2 字体。
- `<main>`：界面。
- `<script>`：字符池 `characters`、随机转换、输入事件、撤销和复制逻辑。

直接编辑 HTML 即可。字符池中的字都有随文件提供的字体；添加新字符时，需要确认字体是否覆盖它们。

没有构建步骤，也没有运行时依赖。若要用本地 HTTP 服务预览，可在仓库目录运行：

```sh
python3 -m http.server 8000
```

然后访问 `http://localhost:8000`。

## 上传到 GitHub

在 GitHub 新建名为 **funny-characters** 的公开仓库，将本目录内的文件上传到仓库根目录。`README.md`、`LICENSE` 和字体许可证已准备好。

也可使用已安装并登录的 GitHub CLI：

```sh
git init -b main
git add .
git commit -m "Add funny-characters Unicode keyboard"
gh repo create funny-characters --public --source=. --remote=origin --push
```

上传后，若需要让同学直接在线使用，可以在仓库 **Settings → Pages** 中选择从 `main` 分支的根目录发布。本项目本身适合静态托管。

## 已验证

2026-09-21 在 macOS 上使用 Chromium 151 测试了本地 HTML 文件：

- 完全离线加载，四种字体全部成功载入，514 个字符均有对应字形。
- 键盘输入、空格、换行、中文输入法连续选字及取消选字。
- 增补平面字符完整删除、光标插入、选区替换、清空、撤销和重做。
- 实际复制后粘贴核对，以及 Clipboard API 不可用时的复制回退。
- 1100、390、320 像素视口布局；没有 JavaScript 错误或外部网络请求。

## 许可证

程序代码采用 [MIT License](LICENSE)。内嵌字体分别采用 **SIL Open Font License 1.1**；完整版权、来源与许可证见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。字体不适用项目的 MIT 许可证。

---

A tiny offline Unicode keyboard toy. Type anything, get random unusual characters, and copy them into a chat. Plain HTML/CSS/JavaScript, embedded fonts, no runtime dependencies.
