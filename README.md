# 火影战力周攻略

火影忍者战力周攻略发布网站。

## 页面说明

| 页面 | 文件 | 用途 |
|------|------|------|
| 展示页 | `index.html` | 给访客看，只读，无修改入口 |
| 管理页 | `admin.html` | 自己用，上传Word文档、发布更新 |

管理页地址：你的域名/admin.html （别告诉别人）

## 部署到 GitHub Pages

### 方法一：网页上传（最简单）

1. 登录 GitHub，点右上角 **+** → **New repository**
2. 仓库名随便填，比如 `naruto-guide`，选 **Public**，点 **Create repository**
3. 在仓库页面点 **uploading an existing file**
4. 把 `index.html` 和 `admin.html` 两个文件拖进去
5. 点底部 **Commit changes**
6. 顶部菜单 **Settings** → 左侧 **Pages**
7. Source 选 **Deploy from a branch**，Branch 选 `main` / `(root)`，点 **Save**
8. 等一两分钟，上面会显示 `Your site is live at https://xxx.github.io/naruto-guide/`

### 方法二：Git 命令行

```bash
git init
git add index.html admin.html
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

然后在 Settings → Pages 里开启 GitHub Pages。

## 使用方法

### 发布攻略

1. 打开 `admin.html`（管理后台）
2. 输入期数标题，比如 "第10期 战力周攻略"
3. 拖拽或点击上传 `.docx` Word 文档
4. 预览确认内容
5. 点 **发布更新**

### 查看攻略

- 访客打开 `index.html` 直接看最新一期
- 右侧历史记录可以切换往期

## 技术说明

- 数据存储在浏览器 localStorage 中
- 使用 mammoth.js 将 Word 文档转换为 HTML
- 纯前端静态页面，不需要服务器
- Tailwind CSS CDN 提供样式
