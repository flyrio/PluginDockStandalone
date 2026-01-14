# Changelog

所有显著变更都将记录在此文件中。
本项目遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/),
并采用 [语义化版本](https://semver.org/lang/zh-CN/)。

## [Unreleased]

### 新增
- 初始化 helloagents 知识库骨架

### 修复
- 修复显示名称与自定义图标路径清空后回退异常
- 优化窗口隐藏器与 Dock 渲染每帧开销，缓解启用插件导致的帧率下降
- 增加自保护限制：禁止隐藏/收纳本插件自身及相关窗口
