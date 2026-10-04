# 四中恋爱日记 · 静态部署包

这个目录可以直接推到 GitHub Pages，不需要任何构建步骤。

## 目录结构

| 文件 | 说明 |
|---|---|
| `index.html` | 游戏本体（242 KB，首屏很小，打开就能出画面） |
| `assets/` | 19 个素材文件（封面 / 立绘 / 背景 / BGM），合计 11.68 MB |
| `.nojekyll` | 关掉 GitHub Pages 的 Jekyll 处理，避免下划线开头的文件被吃掉 |
| `404.html` | 访问不存在的路径时引导回首页 |

素材是**按内容哈希命名并去重**的：同一段音乐被多幕复用也只存一个文件。

## 部署到 GitHub Pages

```bash
# 在仓库根目录
git add .
git commit -m "add galgame"
git push
```

然后仓库 **Settings → Pages**：
- Source 选 `Deploy from a branch`
- Branch 选 `main`、目录选 `/(root)`
- 保存后等 1-2 分钟，访问 `https://<用户名>.github.io/<仓库名>/`

> `index.html` 必须在**仓库根目录**（或你选的那个目录的根），这是 GitHub Pages 的默认首页约定。

## 本地预览

素材用的是相对路径，必须**通过 HTTP 打开**（直接双击 `index.html` 用 file:// 打开，
浏览器会因跨源策略拒绝加载素材）：

```bash
python -m http.server 8000
# 然后打开 http://127.0.0.1:8000/
```

## 体积

- 本部署包：11.92 MB
- 单文件版：27.43 MB
