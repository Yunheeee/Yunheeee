# GitHub 主页配置说明

本目录是一个独立的仓库，用来存放 GitHub Profile README。  
它不属于 `Ext4WslHelper` 项目，请单独创建远端仓库。

## 目录内容

```
Yunheeee-profile/
├── README.md                      # 显示在 GitHub 个人主页顶部的介绍
├── SETUP.md                       # 本说明
└── .github/workflows/snake.yml    # 可选：生成贡献贪吃蛇 SVG（当前未使用）
```

> **当前 README 是极简版**：只保留个人描述。  
> 第 3 节贪吃蛇、第 7 节动态卡片都是可选扩展，不执行也不影响主页。

---

## 1. 创建 Profile 仓库

GitHub 只会在**仓库名与用户名完全一致**、且仓库为 **Public** 时，把 README 显示在个人主页。

1. 打开 <https://github.com/new>
2. Repository name 填：`Yunheeee`
3. 选择 **Public**
4. **不要**勾选 “Add a README file”（本地已经有 README）
5. 点击 **Create repository**

创建后应该能看到仓库地址：

```
git@github.com:Yunheeee/Yunheeee.git
```

## 2. 推送本地内容

在 PowerShell 中执行：

```powershell
cd E:\Workspace\Yunheeee-profile
git init
git add .
git commit -m "profile: add GitHub profile README"
git branch -M main
git remote add origin git@github.com:Yunheeee/Yunheeee.git
git push -u origin main
```

如果本机 SSH key 已经能推送 `Ext4WslHelper`，这里不需要额外配置。

## 3. 可选：启用贡献贪吃蛇

当前 README 没有引用贪吃蛇图片，不需要执行本节。只有以后想在 README 里加回贪吃蛇时再操作。  
工作流已改为仅手动触发，不会定时运行。

推送后：

1. 打开 <https://github.com/Yunheeee/Yunheeee/actions>
2. 如果提示启用 Actions，点击启用
3. 选择左侧 **Generate Snake**
4. 点击 **Run workflow** → **Run workflow**
5. 等待运行完成，仓库会自动生成 `output` 分支

`README.md` 里的贪吃蛇图片读取的就是：

```
https://raw.githubusercontent.com/Yunheeee/Yunheeee/output/github-snake.svg
https://raw.githubusercontent.com/Yunheeee/Yunheeee/output/github-snake-dark.svg
```

首次运行前图片会显示不出来，属于正常现象。

## 4. 完善个人资料

打开 <https://github.com/settings/profile>，建议填写：

| 字段 | 建议值 |
|---|---|
| Name | `Yunheeee`（以后想公开真名再改） |
| Bio | `主线嵌入式开发，浅耕存储技术栈，偶尔烧token造轮子，大模型黑盒开发爱好者` |
| Company | 留空 |
| Location | 留空 |
| Website | 留空，或填 `https://github.com/Yunheeee` |
| Social links | 只保留 GitHub |

Bio 长度约 100 字符，符合 GitHub 的 160 字符限制。

## 5. 置顶仓库

打开个人主页，点击 **Customize your pins**，建议置顶这 3 个原创项目：

- `Ext4WslHelper`
- `sqlite3-file-viewer`
- `AutoInput`

GitHub 最多可置顶 6 个。如果希望展示更多，可以再加：

- `Ext4Fsd`（fork，EXT4 文件系统驱动）
- `OpenWrt-x86_64-firmware`（fork）

但 fork 项目对“个人作品”的说服力较弱，建议优先保留原创项目。

## 6. 补齐仓库描述和 Topics

打开每个仓库首页，点击右侧 **About** 旁的齿轮图标填写 Description 和 Topics：

### Ext4WslHelper

**Description**

```
Access EXT4 SD cards on Windows via WSL2 + usbipd — offline setup, single exe, no install required
```

**Topics**

```
ext4, wsl2, usbipd, windows, sd-card, filesystem, win32, cpp, offline-installer
```

### sqlite3-file-viewer

**Description**

```
Inspect the SQLite3 database file format with a PyQt5 GUI.
```

**Topics**

```
sqlite, file-format, pyqt5, python, database, reverse-engineering
```

### AutoInput

**Description**

```
Serial terminal command auto-input tool — pick a window, then send text line by line.
```

**Topics**

```
serial, uart, automation, pyqt5, python, terminal
```

---

## 7. 可选扩展（当前 README 未使用）

当前 README 是纯文本极简版，没有动态卡片。以下内容仅作为以后扩展参考。

### 动态卡片服务说明

如果以后加回动态卡片，README 可以使用三个第三方服务：

| 用途 | 地址 |
|---|---|
| GitHub 统计 + 语言 | `github-readme-stats-sigma-five.vercel.app` |
| 连续贡献 | `streak-stats.demolab.com` |
| 贡献活动图 | `github-readme-activity-graph.vercel.app` |

官方 `github-readme-stats.vercel.app` 目前经常返回 503，所以使用了可用镜像。  
如果以后镜像也失效，可以：

1. 换回官方地址；
2. 或部署自己的 `github-readme-stats`；
3. 或删掉对应 `<img>`，只保留贪吃蛇和 streak。

### 觉得动态卡片太多

可以按顺序删除：

- 贡献活动图：`<img ... github-readme-activity-graph ...>`
- 连续贡献：`<img ... streak-stats ...>`
- 语言卡片

保留统计卡 + 贪吃蛇即可。

### 修改主题色

`README.md` 中的 `theme=tokyonight` 可换成：

- `github_dark`
- `radical`
- `dracula`
- `onedark`

统计卡、语言卡、streak 建议保持同一个主题。  
注意活动图的主题名是 `tokyo-night`（带连字符），和其他服务的 `tokyonight` 写法不同。

### `Yunheeee.github.io`

这个仓库目前还是 Jekyll 默认模板（标题是 “Your awesome title”），暂时不用管。  
以后如果要做正式个人网站，可以在这个仓库里重做，再把链接填到个人资料的 Website 字段。

---

## 验证清单

- [ ] `https://github.com/Yunheeee` 顶部出现 README
- [ ] 3 个原创项目已置顶
- [ ] 3 个项目的 Description 和 Topics 已补齐
- [ ] 个人资料 Bio 已填写
