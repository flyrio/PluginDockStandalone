# 架构说明

## 总览
```mermaid
flowchart TD
    A[Dalamud Host] --> B[PluginDockPlugin]
    B --> C[PluginDockController]
    C --> D[Dock/Config Windows]
    C --> E[Config 数据]
```

## 关键依赖
- **UI:** ImGui (Dalamud.Bindings.ImGui)
- **配置:** Dalamud IPluginConfiguration
- **资源:** 本地文件与可选网络图标

## 交互流程
```mermaid
sequenceDiagram
    participant User
    participant UI as Dock UI
    participant Cfg as Config
    User->>UI: 编辑显示名称/图标
    UI->>Cfg: 更新配置并保存
```

## 架构决策记录
暂无 ADR 记录。

| adr_id | title | date | status | affected_modules | details |
|--------|-------|------|--------|------------------|---------|
