# Darknet2Caffe
DarkNet下训练的yolo的`.cfg`文件和`.weights`文件转换为Caffe的`.prototxt`文件和`.caffemodel`文件

### 根目录执行命令：
```
python darknet2caffe.py yolov2_tiny_3.cfg yolov2_tiny_3.weights yolov2_tiny_3.prototxt yolov2_tiny_3.caffemodel
```

其中：

1. `yolov2_tiny_3.cfg` --------- 模型结构文件，这里是一个3个类别的目标检测模型

2. `yolov2_tiny_3.weights` ----- 训练好的模型权重文件

3. `yolov2_tiny_3.prototxt` ---- 待生成的Caffe框架下的模型结构文件

4. `yolov2_tiny_3.caffemodel` -- 待生成的Caffe框架下的模型权重文件


注：

0. 上面我准备好的4个文件下载链接：链接：https://pan.baidu.com/s/1IvThiM1BpkQ8HwNsKdhGCg 密码：0ajp

1. 修改`darknet2caffe.py`中的Caffe路径（需要该Caffe已经添加YOLO相关的层，https://github.com/lwplw/caffe_yolov2）

2. 修改`yolov2_tiny_3.prototxt`文件（和Caffe下region层的实现有关）

将第一层
```
input: "data"
input_dim: 1
input_dim: 3
input_dim: 416
input_dim: 416
```

修改为：

```
layer {
  name: "data"
  type: "Input"
  top: "data"
  input_param { shape: { dim: 1 dim: 3 dim: 416 dim: 416 } }
}

```

### Reference：
> https://github.com/marvis/pytorch-caffe-darknet-convert

> https://github.com/lwplw/caffe_yolov2
