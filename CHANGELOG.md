# Changelog

本文件记录 `yolov13_obb` 仓库的关键变更，便于实验复盘与论文写作追踪。

## [Unreleased]

- 修复 OBB 验证阶段指标打印报错：`TypeError: not all arguments converted during string formatting`。
  - 对齐 OBB 指标键数量，补齐 `metrics/mAP75(B)`。
- 完成一次 `yolov13n-obb` 烟测训练验证（1 epoch），确认训练与验证流程可正常运行。
  - 训练配置：`imgsz=640`, `batch=48`, `optimizer=SGD`。
  - 数据集加载正常，AMP 自检通过。
- 训练注意事项：保持原版 AMP 自检逻辑时，需要本地可用的 `yolov13n.pt` 权重文件。

## [0.1.0] - 2026-04-25

### Added

- 新建独立仓库 `yolov13_obb`。
- 新增仓库级 `.gitignore`：
  - 忽略训练输出（`runs/`, `wandb/`, `mlruns/`）
  - 忽略缓存与环境目录（如 `__pycache__/`, `.venv/`）
  - 忽略模型导出产物（如 `*.pt`, `*.onnx`, `*.engine`）
- 新增 OBB 模型配置：
  - `ultralytics/cfg/models/v13/yolov13-obb.yaml`

### Changed

- 将 OBB 适配说明写入 `README.md`（仅保留改动点与训练入口）。
- 保留上游文档快照：`README_YOLO13.MD`。

### Notes

- 当前 OBB 适配为最小可运行版本：保持 YOLOv13 原 backbone/neck，末端检测头由 `Detect` 切换为 `OBB`。
- 支持 scale：`n/s/m/l/x`。

---

## 版本说明

- `0.1.0`：仓库初始化 + YOLOv13 最小 OBB 适配基线。
