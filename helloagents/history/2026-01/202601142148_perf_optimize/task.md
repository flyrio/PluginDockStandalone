# 方案任务: 启用即掉帧的性能优化

范围: `helloagents/plan/202601142148_perf_optimize/`

---

## 1. 隐藏器热路径优化
- [√] 1.1 当隐藏列表为空且无临时隐藏时，跳过 `ApplyHiddenImGuiWindows` 的执行，依据 why.md#需求范围 与 why.md#验收标准
- [√] 1.2 移除每帧按名称调用 `ImGui.SetWindowPos/SetWindowCollapsed` 的逻辑，改为仅执行硬隐藏，依据 why.md#需求范围 与 why.md#风险与边界
- [√] 1.3 避免隐藏器每帧分配（如 `ToArray()`），依据 why.md#验收标准

## 2. Dock 渲染缓存
- [√] 2.1 为已加载插件列表与 `InternalName -> Plugin` 字典增加短周期缓存，避免每帧排序与字典构建，依据 why.md#需求范围
- [√] 2.2 复用 Dock 渲染临时列表，减少每帧分配，依据 why.md#验收标准

## 3. 图标加载 IO 优化
- [√] 3.1 调整图标加载逻辑：优先命中纹理缓存，减少每帧 `File.Exists`，依据 why.md#需求范围

## 4. 验证与回归
- [√] 4.1 编译验证（`dotnet build`），确保无语法/引用错误
- [-] 4.2 手动验证：启用插件但不打开任何窗口，不再明显掉帧，依据 why.md#验收标准
  > 备注: 需要在游戏内手动验证/对比（建议对比禁用插件时的帧率与 CPU 占用）
- [-] 4.3 手动验证：窗口隐藏器仍可可靠隐藏目标窗口且无明显闪烁，依据 why.md#验收标准
  > 备注: 需要在游戏内手动验证（特别是隐藏列表较多的场景）

## 5. 文档与记录
- [√] 5.1 更新 `helloagents/wiki/modules/plugindock.md` 记录性能优化点
- [√] 5.2 更新 `helloagents/CHANGELOG.md` 记录性能修复/优化
