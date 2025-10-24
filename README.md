## Label-Studioサーバーを立てるCLI。
```
label-studio start --host 127.0.0.1 --port 8080
```

http://127.0.0.1:8080 or http://localhost:8080


## Google Colabo上でUltralyticsのYoloを構築。

### Ultralyticsをインストール
```
!pip install ultralytics
```

### data.yamlを作成
```
%%writefile /content/dataset/data.yaml
train: /content/dataset/images/train
val: /content/dataset/images/val

nc: 1
names: ['Table']
```

### モデルのトレーニング
```
from ultralytics import YOLO

model = YOLO("yolov8n-obb.pt")

model.train(
    data="/content/dataset/data.yaml",
    epochs=50,
    imgsz=640,
    batch=8
)
```


