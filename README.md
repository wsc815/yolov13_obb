# yolov13_obb

这个目录是我在 YOLOv13 基础上做 OBB 适配的实验版本。
原始项目说明保留在 `README_YOLO13.MD`，这里仅记录和 OBB 相关的改动与使用方法。

## 我改了什么

目前只做了最小改动，先保证能跑通：

1. 新增模型配置文件：
   - `ultralytics/cfg/models/v13/yolov13-obb.yaml`

2. 配置思路：
   - 直接沿用 `yolov13.yaml` 的 backbone 和 neck；
   - 只把最后一层从 `Detect` 换成 `OBB`；
   - 对应输出头：`[[23, 27, 31], 1, OBB, [nc, 1]]`

3. scale：
   - 支持 `n/s/m/l/x`

## 怎么开始 OBB 训练

先进入项目目录并准备好环境，然后执行：

```bash
yolo task=obb mode=train \
  model=ultralytics/cfg/models/v13/yolov13n-obb.yaml \
  data=/path/to/data.yaml \
  imgsz=640 epochs=200 batch=48 device=0
```

如果要换规模，把 `model` 改成对应文件名即可：
- `yolov13n-obb.yaml`
- `yolov13s-obb.yaml`
- `yolov13m-obb.yaml`
- `yolov13l-obb.yaml`
- `yolov13x-obb.yaml`

## 备注

这个版本目前是“先跑通”的阶段，后面再逐步补充实验对比和改进记录。
