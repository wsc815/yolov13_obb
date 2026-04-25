# Changelog

本文件记录 `yolov13_obb` 仓库的关键变更，便于实验复盘与论文写作追踪。

## [Unreleased]

- 修复 AMP 自检流程：当本地缺少 `yolov13n.pt` 时，不再因 `FileNotFoundError` 崩溃；
  现在会跳过 AMP 检查并继续训练。

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
