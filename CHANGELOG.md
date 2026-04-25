# Changelog

记录 `yolov13_obb` 的关键变更，主要用于实验复盘。

## Unreleased

- 修了 OBB 验证阶段的指标打印报错（`TypeError: not all arguments converted during string formatting`）。
  - 原因是 OBB 指标键数量和返回结果数量不一致。
  - 现在已补齐 `metrics/mAP75(B)`，验证阶段可正常打印。
- 跑通了 `yolov13n-obb` 的 1 epoch 烟测，训练和验证流程都正常。
- 备注：当前保持原版 AMP 自检逻辑，训练前请准备本地 `yolov13n.pt`（AMP 检查会用到）。

## 0.1.0 - 2026-04-25

- 初始化独立仓库 `yolov13_obb`。
- 新增 OBB 配置：`ultralytics/cfg/models/v13/yolov13-obb.yaml`。
- OBB 适配采用最小改动策略：
  - 沿用 YOLOv13 原 backbone/neck；
  - 仅将检测头由 `Detect` 切换为 `OBB`。
- 支持 scale：`n/s/m/l/x`。
- 补充仓库级 `.gitignore`，忽略训练产物和常见缓存文件。
