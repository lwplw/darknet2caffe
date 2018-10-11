# darknet2caffe
DarkNet下训练的yolo的.cfg文件和.weights文件转换为Caffe的.prototxt文件和.caffemodel文件

## 根目录执行命令：
`python darknet2caffe.py yolov2_tiny_3.cfg yolov2_tiny_3.weights yolov2_tiny_3.prototxt yolov2_tiny_3.caffemodel`

其中，yolov2_tiny_3.prototxt yolov2_tiny_3.caffemodel为要生成的文件名

注：修改darknet2caffe.py中的Caffe路径

## Reference：
> https://github.com/marvis/pytorch-caffe-darknet-convert

> https://github.com/lwplw/caffe_yolov2
