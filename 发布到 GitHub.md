# 发布到 GitHub（两种做法，选一种）

仓库目录已经准备好了：`C:\Users\Aa819\Documents\deepseek-harness\Z3d-github`
里面就是完整的网站 + README + 许可证 + 文档，不需要再改任何东西。

---

## 方法一：网页上传（不用装任何东西，推荐）

1. 登录 GitHub，点右上角 **+** → **New repository**
2. 填仓库名，比如 `z3d`，选 **Public**，**不要**勾 "Add a README file"（我们自带），点 **Create repository**
3. 在新页面点 **uploading an existing file**（或直接访问
   `https://github.com/<你的用户名>/z3d/upload/main`）
4. 打开桌面文件夹 `Z3d-github`，**全选里面所有内容和文件夹**，拖进浏览器上传框
   - `index.html`、`manifest.webmanifest`、几个 png、`404.html`、`netlify.toml`、`vercel.json`、`README.md`、`LICENSE`、`.gitignore`、`docs/` 文件夹、`.nojekyll`
   - 注意：`.nojekyll`、`.gitignore` 是隐藏文件。Windows 资源管理器里先
     「查看 → 显示 → 隐藏的项目」把它们显出来，否则会漏传（漏了也不影响使用）
5. 页面底部点 **Commit changes**
6. 开启在线访问：**Settings** → 左侧 **Pages** → Source 选 **Deploy from a branch** →
   Branch 选 **main**、目录选 **/ (root)** → **Save**
7. 等 1–2 分钟，刷新该页，顶部会出现你的网址：
   `https://<你的用户名>.github.io/z3d/`

---

## 方法二：命令行（装了 Git 之后）

这台电脑已经装了 Git（2.9.3），但还没有登录 GitHub 的凭据。
第一次推送会弹窗要你登录（浏览器授权），或者用 Personal Access Token 当密码。

```powershell
cd C:\Users\Aa819\Documents\deepseek-harness\Z3d-github

git init
git add -A
git commit -m "Z3d: 浏览器里的三维函数绘图"
git branch -M main
git remote add origin https://github.com/<你的用户名>/z3d.git
git push -u origin main
```

推送完同样去 **Settings → Pages** 开启（步骤同上第 6 步）。

---

## 发布之后

- **网址**：`https://<用户名>.github.io/<仓库名>/`
- **改内容**：改完文件再 `git add -A && git commit -m "..." && git push`，
  Pages 会在 1 分钟内自动更新
- **换域名**：Settings → Pages → Custom domain
- **国内访问**：GitHub Pages 有时偏慢，可以把同一份文件再传到 Gitee Pages 或 Netlify

## 小提示

- 仓库必须是 **Public**，免费账号才能开 Pages
- 根目录必须有 `index.html`，我们的目录结构已经满足
- 如果打开是 404，检查 Pages 里的分支是不是 `main`、目录是不是 `/ (root)`
- 分享卡片（微信里显示标题和缩略图）依赖 `og.png` 和 `<meta property="og:*">`，
  已经写好；换成自己的域名后卡片仍然有效
