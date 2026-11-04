# 扫雷 · MINESWEEPER

一个不依赖任何框架的单文件扫雷游戏，深色界面、可调难度、首击安全，支持桌面与移动端。

> 在线试玩：https://dgtghsfv.github.io/minesweeper/

## 特性

- **三档经典难度**：初级 9 × 9 / 10 雷，中级 16 × 16 / 40 雷，高级 30 × 16 / 99 雷
- **自定义雷区**：宽度 5–30 列、高度 5–24 行，雷数上限随棋盘大小变化
- **首击安全**：第一格及周围 8 格不会埋雷
- **流畅操作**：空白区域自动展开；在数字格上再次点击，旗数匹配时快速展开相邻格
- **移动端适配**：轻点翻开，长按插旗，大棋盘可横向滑动
- **键盘可玩**：方向键移动，`Space` 翻开，`F` 插旗
- **对局信息**：剩余雷数、计时器、个人最佳成绩
- **本地记录**：各难度最佳成绩通过 localStorage 保存在浏览器本地
- **细节体验**：音效开关、玩法说明、胜负结算、新纪录提示
- **零依赖**：一个 `index.html`，无需安装、无需构建

## 操作

| 操作 | 桌面端 | 移动端 |
| --- | --- | --- |
| 翻开格子 | 左键点击 | 轻点 |
| 插旗 / 取消旗 | 右键、`Shift` + 点击 | 长按 |
| 快速展开 | 点击已翻开的数字格 | 轻点已翻开的数字格 |
| 移动焦点 | 方向键 | — |
| 翻开 / 插旗 | `Space` / `F` | — |

数字表示周围 8 格中的地雷数量。当周围旗子数量与数字一致时，再次点击数字即可展开其余相邻格。

## 本地运行

直接双击打开 `index.html` 即可。

也可以启动一个本地静态服务器：

```bash
python -m http.server 8000
```

然后访问 `http://localhost:8000`。

## 发布到 GitHub Pages

### 1. 新建仓库

在 GitHub 上新建一个公开仓库，例如 `minesweeper`，不要勾选自动生成 README。

### 2. 提交并推送

在项目根目录执行：

```bash
git init
git add index.html README.md .gitignore .nojekyll
git commit -m "feat: add minesweeper game"
git branch -M main
git remote add origin https://github.com/<your-name>/<repo>.git
git push -u origin main
```

注意：这个工作区里还有其他文件，请按上面的文件名逐个 `git add`，不要使用 `git add .`。

如果使用 GitHub CLI，可以在完成上面的 `git commit` 之后，用下面的命令创建远程仓库并推送：

```bash
gh repo create <repo> --public --source=. --remote=origin --push
```

### 3. 开启 Pages

1. 打开 GitHub 仓库的 **Settings**
2. 左侧选择 **Pages**
3. **Build and deployment** → **Source** 选择 **Deploy from a branch**
4. 分支选择 **main**，目录选择 **/(root)**
5. 点击 **Save**

稍等片刻，站点会发布在：

```text
https://<your-name>.github.io/<repo>/
```

## 项目结构

```text
.
├── index.html    # 完整游戏（HTML + CSS + JavaScript）
├── README.md
├── .gitignore
└── .nojekyll     # 让 GitHub Pages 跳过 Jekyll 处理
```

## 说明

- 游戏不需要后端，所有逻辑都在浏览器中运行。
- 最佳成绩保存在浏览器 localStorage 中，不会上传到服务器。
- 项目暂未指定开源许可证。如需 MIT 等许可证，可以再添加 `LICENSE` 文件。
