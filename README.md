# 火影战力周攻略

火影忍者战力周攻略发布网站。访客打开网站直接看最新攻略，管理员通过后台更新内容。

## 页面说明

| 页面 | 文件 | 用途 |
|------|------|------|
| 展示页 | `index.html` | 给访客看，只读，从 data.json 读取内容 |
| 管理页 | `admin.html` | 自己用，上传Word文档、导出 data.json |
| 数据文件 | `data.json` | 攻略数据文件，发布后生成 |

管理页地址：你的域名/admin.html （别告诉别人）

## 工作原理

```
你（管理员）                 GitHub Pages              访客
   |                            |                       |
   | 1. 打开 admin.html         |                       |
   | 2. 上传 Word 文档          |                       |
   | 3. 点发布 → 下载 data.json |                       |
   | 4. 上传 data.json 到仓库 → | ← data.json           |
   |                            | index.html            | → 打开网站看到内容
   |                            | admin.html            |
```

- 内容存在 `data.json` 文件里，所有人访问都读同一个文件
- 手机、电脑、任何设备打开都能看到同样的内容
- 更新 = 重新上传一次 data.json

## 部署到 GitHub Pages

### 第一次部署

1. 登录 GitHub，点右上角 **+** → **New repository**
2. 仓库名随便填，比如 `naruto-guide`，选 **Public**，点 **Create repository**
3. 在仓库页面点 **uploading an existing file**
4. 把 `index.html`、`admin.html`、`data.json` 三个文件拖进去
5. 点底部 **Commit changes**
6. 顶部菜单 **Settings** → 左侧 **Pages**
7. Source 选 **Deploy from a branch**，Branch 选 `main` / `(root)`，点 **Save**
8. 等一两分钟，上面会显示 `Your site is live at https://xxx.github.io/naruto-guide/`

### 每周更新攻略

1. 打开 `https://你的域名/admin.html`
2. 输入期数标题，上传 Word 文档（.docx）
3. 预览没问题后点 **发布更新**
4. 浏览器会自动下载 `data.json` 文件
5. 回到 GitHub 仓库，点 **Add file** → **Upload files**
6. 把刚下载的 `data.json` 拖进去，点 **Commit changes**
7. 等几十秒，刷新网站就能看到新内容了

## 管理后台功能

- **发布攻略**：上传 Word 文档，转换为网页格式
- **导出 data.json**：手动导出当前所有数据
- **导入 data.json**：从 data.json 恢复数据（换电脑时用）
- **历史记录管理**：删除单期、清空全部
- **同期数覆盖**：标题相同会询问是否覆盖

## 文件结构

```
naruto-guide/
├── index.html      # 展示页（访客看）
├── admin.html      # 管理页（你用）
├── data.json       # 攻略数据（发布后生成）
└── README.md       # 说明文档
```

## 技术说明

- 纯前端静态页面，不需要服务器
- 使用 mammoth.js 将 Word 文档转换为 HTML
- Tailwind CSS CDN 提供样式
- 数据格式：JSON 数组，最新一期在最后
