# 数据说明

## 概述
配置数据由 Dalamud 插件框架持久化，主要结构为 Config 与 DockItem。

---

## 数据结构

### Config
**说明:** 插件全局配置。

| 字段 | 类型 | 说明 | 备注 |
|------|------|------|------|
| DockEnabled | bool | Dock 是否启用 | |
| DockOpen | bool | Dock 是否展开 | |
| IconSize | float | 图标大小 | |
| IconSpacing | float | 图标间距 | |
| DockHeaderIconPath | string? | 头部图标路径 | |
| Items | List<DockItem> | Dock 条目列表 | |
| WindowHiderPresets | List<WindowHiderPreset> | 窗口隐藏预设 | |

### DockItem
**说明:** Dock 中的单个条目。

| 字段 | 类型 | 说明 | 备注 |
|------|------|------|------|
| Kind | enum | 条目类型 | Plugin/ImGuiWindow/Command |
| InternalName | string | 内部名称 | 插件或窗口标识 |
| CustomDisplayName | string? | 自定义显示名 | 为空则回退原名 |
| CustomIconPath | string? | 自定义图标路径 | |
| ClickCommand | string? | 点击命令 | |
| ContextMenuMacros | List<DockItemMacro> | 右键菜单宏 | |
