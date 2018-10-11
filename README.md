# Darknet2Caffe
DarkNet下训练的yolo的.cfg文件和.weights文件转换为Caffe的.prototxt文件和.caffemodel文件

### 根目录执行命令：
```
python darknet2caffe.py yolov2_tiny_3.cfg yolov2_tiny_3.weights yolov2_tiny_3.prototxt yolov2_tiny_3.caffemodel
```

其中：

1. yolov2_tiny_3.cfg --------- 模型结构文件，这里是一个3个类别的目标检测模型

2. yolov2_tiny_3.weights ----- 训练好的模型权重文件

3. yolov2_tiny_3.prototxt ---- 待生成的Caffe框架下的模型结构文件

4. yolov2_tiny_3.caffemodel -- 待生成的Caffe框架下的模型权重文件


注：
1. 修改darknet2caffe.py中的Caffe路径（需要该Caffe已经添加YOLO相关的层，https://github.com/lwplw/caffe_yolov2）

2. 修改yolov2_tiny_3.prototxt文件（和Caffe下region层的实现有关）

将最后一层
```
layer {
    bottom: "layer15-conv"
    top: "layer16-region"
    name: "layer16-region"
    type: "Region"
    region_param {
        anchors: "1.08,1.19,  3.42,4.41,  6.63,11.38,  9.42,5.11,  16.62,10.52"
        classes: 3
        num: 5
    }
}
```

修改为：

```
layer {
  name: "region1"
  type: "Region"
  bottom: "layer15-conv"
  top: "region1"
  region_param {
    classes: 3
    coords: 4
    boxes_of_each_grid: 5
    softmax: true
  }
}
```

### Reference：
> https://github.com/marvis/pytorch-caffe-darknet-convert

> https://github.com/lwplw/caffe_yolov2
