# 模型转换



- 模型转换是将Pytorch，MindSpore等模型转换为 `ONNX` 框架

>[!note|label: 什么是ONNX框架]
>ONNX是一种针对机器学习所设计的开放式的文件格式，用于存储训练好的模型。它使得不同的人工智能框架(如Pytorch, MXNet)可以采用相同格式存储模型数据并交互。 ONNX的规范及代码主要由微软，亚马逊 ，Facebook 和 IBM 等公司共同开发，形成强大的深度学习开源联盟，并将源代码托管在[Github](https://github.com/ONNX)，目前官方支持加载ONNX模型并进行推理的深度学习框架有Caffe2, Pytorch, MXNet，ML.NET，TensorRT 和 Microsoft CNTK， TensorFlow也有非官方的支持ONNX。

- 目前平台支持 `Pytorch`， `MindSpore`， `TensorFlow`，` PaddlePaddle`， `MXNet` 五种框架到 `ONNX` 的转换
- 从项目中的 `模型`->`模型转换`->`创建模型转换任务` 即可创建

<img src="_media/model/convert-create.png" width = "800" alt="traindetail" align=middle />

- 创建成功后，等待模型转换任务完成即可下载转换后的模型

<img src="_media/model/convert-list.png" width = "800" alt="traindetail" align=middle />