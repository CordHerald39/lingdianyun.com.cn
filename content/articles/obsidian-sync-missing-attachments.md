---
title: "Obsidian Sync 笔记有了附件没来：文件类型、大小与同步状态检查"
description: "Obsidian Sync 笔记有了附件没来：文件类型、大小与同步状态检查。按适用条件、操作步骤、失败分支和官方参考逐项检查。"
date: "2026-10-06"
category: "tutorials"
updated: "2026-10-06"
author: "零点云 内容编辑"
draft: false
label: "跨境办公学习开发者服务"
---

多台设备用 Obsidian 官方 Sync 时，Markdown 笔记已经出现，图片、音频、视频或 PDF 却没有跟来。处理方向是：只在 Sync 核心插件里核对选择性同步、方案允许的单文件大小、同步是否暂停以及排除列表；不要把 iCloud、Git 插件或其它网盘当成同一套机制。改排除项或断开远程库前，先自行保留本地库副本，不要为了“清附件”去删远程仓库。设置说明见 [Sync settings and selective syncing](https://github.com/obsidianmd/obsidian-help/blob/master/en/Obsidian%20Sync/Sync%20settings%20and%20selective%20syncing.md)。

## 先确认连的是官方远程库且同步未暂停

创建并连接远程库后，由 Sync 核心插件管理该库。打开 Settings → Sync，先看 Remote vault：可 Disconnect，也可用 Manage 查看账号能访问的远程库（含协作共享库）。若远程库落在第三方同步服务中，会出现红色错误，需按官方切换到 Obsidian Sync 的说明处理，本文不把第三方路径与官方 Sync 混写。

同一页的 Sync status 显示当前状态，并提供 Pause 或 Resume。若为暂停，附件不会继续过来，应 Resume 后再等。Device name 要为当前设备指定独特名称，便于在同步日志里区分活动；该设置与选择性同步一样按设备单独保存。本页把设备名与日志关联，但未逐步写出打开日志的按钮，缺附件时仍以本页有的状态、类型、大小和排除项为主。Storage usage 用进度条显示占用，服务端处理可能导致用量最多约 30 分钟才更新，不要刚传完就按瞬时数字判断已满。需要协助时，可用 Contact support 中的 Copy debug info，按官方联系支持的途径提交，不要在未保留本地副本的情况下断开或清空远程库。

## 按文件类型和方案大小核对附件

同步到远程库的文件会计入存储上限。默认情况下，选择性同步针对 Images、Audio、Videos、PDFs。其它类型须打开 Sync all other types 才会同步。笔记能到、附件不到，常见分支是：附件不在上述四类且未打开该项，或单文件超过方案上限。

更改步骤：打开 Settings → Sync，在 Selective sync 下启用要同步的类型，然后重启应用；手机或平板可能需要强制退出后再打开。官方说明：Standard 方案单文件最大 5 MB，Plus 方案最大 200 MB。超过上限的附件不会按该方案同步，不能靠反复 Pause、Resume 突破限制。材料未写出超限时的提示原文，故不以猜测弹窗为准。

Vault configuration sync 管的是主设置、外观、主题与代码片段、快捷键、核心插件列表等，不是附件文件本身。社区插件相关项需另行启用，与“正文有了图没来”不是同一开关。冲突处理（自动合并或生成冲突文件）也须每台设备分别设置，它解决的是多端同时改同一文件，不能替代类型与大小检查。

## 排除列表、隐藏文件与改完仍缺失

默认会同步库内文件和文件夹。排除某文件夹：Settings → Sync，在 Excluded folders 旁选 Manage，勾选文件夹后选 Done；要从排除列表去掉，使用文件夹名旁的关闭按钮。把文件加入 Excluded files 不会从远程库删除已经同步过的副本，排除项仍可能占额度，应在首次同步前配置，而不是事后靠删远程库腾地方。

以点号开头的文件和文件夹视为隐藏，不同步；唯一例外是库的配置文件夹 `.obsidian`。因此 `.git`、`.gitignore`、`.vscode`、`.idea` 等不会走 Sync。File recovery 插件的快照也不通过 Sync 同步。Sync 设置本身不会跨设备同步，每台都要单独配置选择性同步；只在一台打开图片同步、另一台未开，就会出现一边有附件、一边只有笔记。

改完类型后必须重启（移动端或需强制退出）。多设备改库配置时，先在作为基准的设备启用并重启、等待同步到远程，再在其它设备启用、等待下载后重启。若附件仍缺失：核对是否被排除、是否落在隐藏路径、是否超过 5 MB 或 200 MB、同步是否 Pause、用量是否已满（注意最多约 30 分钟的更新延迟）。已删除内容可在 Deleted files 用 View 或 Restore 查看，细节见版本历史相关说明。
