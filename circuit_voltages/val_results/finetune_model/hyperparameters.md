## YOLOv12 Training Parameters

### Core Training Parameters
| Parameter | Type | Default/Example | Description |
|-----------|------|----------------|-------------|
| `model` | str | `"yolov12n.yaml"` | Path to model config file |
| `data` | str | `"coco.yaml"` | Path to dataset config file |
| `epochs` | int | `100` | Total training epochs |
| `batch` | int | `16` | Batch size (auto-adjustable) |
| `imgsz` | int | `640` | Input image size |
| `workers` | int | `8` | Data loading threads |

### Data Augmentation
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `multi_scale` | bool | `False` | Enable random image scaling |
| `rect` | bool | `False` | Rectangular training |
| `augment` | bool | `True` | Basic augmentations |
| `mosaic` | float | `1.0` | Mosaic probability |
| `mixup` | float | `0.0` | MixUp probability |

### Optimizer
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `optimizer` | str | `"auto"` | `SGD`/`AdamW`/`auto` |
| `lr0` | float | `0.01` | Initial learning rate |
| `momentum` | float | `0.937` | SGD momentum |
| `weight_decay` | float | `0.0005` | L2 regularization |
| `warmup_epochs` | float | `3.0` | LR warmup epochs |

### Loss Function
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `box` | float | `7.5` | Box loss weight |
| `cls` | float | `0.5` | Class loss weight |
| `dfl` | float | `1.5` | DFL loss weight |

### Advanced Control
| Parameter | Type | Description |
|-----------|------|-------------|
| `device` | str | `"cuda:0"` | Training device |
| `resume` | bool | Resume training |
| `cache` | str | `"ram"`/`"disk"` | Dataset caching |
| `close_mosaic` | int | Disable mosaic last N epochs |

### Key Usage Example
```python
args = dict(model="yolov12n.yaml", data="circuit.yaml", 
            epochs=100, imgsz=640, batch=16)
trainer = DetectionTrainer(overrides=args)
```