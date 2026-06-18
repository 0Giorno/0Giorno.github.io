# Hugo + PaperMod 博客使用说明

## 项目结构

```
MyHomepage/
├── hugo.toml                    # 站点配置文件
├── content/                     # 内容目录
│   ├── _index.md               # 首页内容
│   ├── books.md                # 读书笔记页面
│   ├── photography.md          # 摄影集页面
│   ├── life.md                 # 生活记录页面
│   ├── papers.md               # 论文笔记页面
│   ├── search.md               # 搜索页面
│   └── posts/                  # 博客文章目录
│       └── example.md          # 文章示例
├── layouts/                    # 自定义布局
│   ├── index.html              # 首页布局
│   └── _default/
│       └── taxonomy.html       # 分类页布局
├── assets/css/extended/
│   └── custom.css              # 自定义样式
└── static/
    └── images/                 # 图片资源目录
        └── hero.jpg            # 首页背景图
```

---

## 一、修改页面布局

### 1. 修改首页布局

编辑 `layouts/index.html` 文件。当前首页是全屏英雄图模式。

### 2. 修改样式

编辑 `assets/css/extended/custom.css` 文件：

```css
/* 修改导航栏背景 */
.header {
    background: rgba(0,0,0,0.7) !important;
}

/* 修改首页标题样式 */
.hero-content h1 {
    font-size: 4rem;
}

/* 修改文章卡片样式 */
.post-entry {
    border-radius: 12px;
}
```

### 3. 修改导航菜单

编辑 `hugo.toml` 文件：

```toml
[menu]
  [[menu.main]]
    name = "读书笔记"
    url = "/books/"
    weight = 1

  [[menu.main]]
    name = "🔍"
    url = "/search/"
    weight = 5
```

---

## 二、修改内容排版

### 1. 修改首页内容

编辑 `content/_index.md`：

```markdown
---
title: "你的名字"
emoji: "🌍"
description: "你的个人简介"
---
```

### 2. 修改页面内容

编辑对应页面的 `.md` 文件，例如 `content/books.md`：

```markdown
---
title: "读书笔记"
date: 2026-06-18
description: "阅读心得"
---

## 最近阅读

- 《深入理解计算机系统》
- 《代码大全》
```

### 3. 发布新文章

在 `content/posts/` 目录下创建 `.md` 文件：

```markdown
---
title: "文章标题"
date: 2026-06-18
draft: false
tags: ["标签1", "标签2"]
categories: ["分类"]
description: "文章描述"
---

文章正文...
```

---

## 三、上传笔记和摄影集

### 1. 添加读书笔记

编辑 `content/books.md` 文件，使用 Markdown 语法编写内容。

### 2. 添加摄影集

编辑 `content/photography.md` 文件，插入图片：

```markdown
---
title: "摄影集"
date: 2026-06-18
---

## 风景摄影

![照片标题](/images/photo1.jpg)
![照片标题](/images/photo2.jpg)
```

### 3. 上传图片

将图片放入 `static/images/` 目录：
- 首页背景图：`static/images/hero.jpg`
- 文章图片：`static/images/xxx.jpg`

---

## 四、常用命令

| 操作 | 命令 |
|------|------|
| 启动本地服务 | `D:\hugo\bin\hugo.exe server` |
| 预览草稿 | `D:\hugo\bin\hugo.exe server -D` |
| 构建静态文件 | `D:\hugo\bin\hugo.exe` |
| 指定端口 | `D:\hugo\bin\hugo.exe server -p 8080` |

---

## 五、配置说明

### hugo.toml 关键配置

```toml
baseURL = 'https://your-site.com/'   # 站点域名
title = '我的博客'                   # 站点标题
theme = ["PaperMod"]                 # 使用的主题

[params]
  defaultTheme = "auto"              # 主题模式: auto/light/dark
  enableSearch = true                # 启用搜索功能
```

### 主题模式设置

- `auto`: 根据系统设置自动切换
- `light`: 始终浅色模式
- `dark`: 始终深色模式

---

## 六、注意事项

1. 图片文件名不要包含中文和特殊字符
2. 文章草稿设置 `draft: true` 不会在首页显示
3. 修改配置文件后服务器会自动重建
4. 首次构建需要等待 Hugo 下载依赖

---

如有问题，请查看 PaperMod 官方文档：
- https://github.com/adityatelange/hugo-PaperMod
