# Couplets

## 项目名称：平仄平仄平平仄

### 主要功能:

在网页上输入上联，自动输出下联

### 实现原理：

项目使用Tensor2Tensor，对于系统中可以支持的问题，直接给系统设置好下面的信息就可以运行了：数据，问题(problem)，模型，超参集合，运行设备。这里的实现其实是采用了设计模型中的工厂模式，即给定一个问题名字，返回给相应的处理类；给定一个超参名，返回一套超参的对象。

#### 1、数据收集

从GitHub网站下载couplet v1.0 release版本的数据，并解压。
GitHub网站：https://github.com/wb14123/couplet-dataset/releases
文件名：couplet.tar.gz

#### 2、下载Tensor2Tensor库v1.2.9版本

在Resources目录下，
git clone https://github.com/tensorflow/tensor2tensor.git
git checkout v1.2.9

#### 3、数据处理

Couplet数据解压后，有两个文件夹，分别存放train和test的上下联数据。In为上联，out为下联。在训练过程中，我们只需对train的数据进行预处理。

##### 4、数据生成

运行bash data_gen.sh脚本，完成数据生成工作。

##### 5、数据训练

###### 1.	在Resources目录下，创建output目录存放训练结果。

###### 2.	修改train.sh脚本内容，如train_steps，batch_size等为你想要的数值。

###### 3.	运行bash train.sh脚本，完成数据处理工作。

###### 4.	数据训练完成，则在output目录下生成训练数据。

##### 6、使用模型

在decoder目录下创建q.txt，里面写入上联（字间需空格）
运行decoder.sh

### 实现网页交互

运行main.py
浏览器里浏览http://127.0.0.1:8080
