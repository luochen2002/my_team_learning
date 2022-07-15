# Task01 初识人工智能视觉应用及OpenVINO工具套件

## 1 我们为什么需要人工智能

### 1.1 课程介绍

- 课程目标：视觉识别是人工智能中重要的一个版块，可应用于安防、医疗、金融、手机、交通等领域。本课程主要对OpenVINO™组件进行概括性介绍，演示运行相关组件；它是一款免费软件，提供大量的开源资源，包括应用示例和场景演示等。在此阶段了解人工智能和OpenVINO的工具套件，为AI应用选择最佳的Intel平台，并使用Intel产品构建AI应用

- 课程内容：

  1. **初级课程：**了解人工智能和OpenVINO的工具套件，为AI应用选择最佳的Intel平台，以及如何使用Intel软件工具等产品的构建整个AI应用，从零开始讲解所有AI的应备知识、相关技术、Intel为每种应用场景推荐的平台和软件工具

  2. **中级课程：**深入了解OpenVINO的工具套件，讲解演示OpenVINO，并且练习使用所有的可用的工具
  3. **高级课程：**介绍如何使用Intel平台和工具，在系统层面构建实际可扩展的AI产品

### 1.2 初级课程目录

OpenVINO 100 **– Course agenda**

- **Lesson 1:** Introduction, why do we need Artificial Intelligence (AI).
- **Lesson 2:** What is Video, what is computer vision, how do we accelerate it on modern computers.
- **Lesson 3:** How to accelerate Video processing
- **Lesson 4:** How to accelerate Neural Network for vision applications
- **Lesson 5:** Video Analytics pipeline
- **Lesson 6:** Demos, OpenVINO at work
- **Lesson 7:** The full flow, from Data to a product using Intel tools-Part 1.
- **Lesson 8:** The full flow, from Data to a product using Intel tools-Part 2.
- **Lesson 9:** Summary, intro to next course (200)

### 1.3 OpenVINO套件简述

​		OpenVINO的全称是：`Open Visual inference and Neural network Optimization`。它是英特尔®于2018年发布开源且免费商用的软件包，主要应用于计算机视觉，实现神经网络模型优化和推理计算加速，助理AI开发者快速进行应用程序或解决方案开发，可解决视觉模拟、自动语音识别、自然语言处理、推荐系统等多种任务。

### 1.4 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_1.png"
         alt="summary_1"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


- AI是我们管理物联网收集的海量数据的唯一方法
- AI将彻底改变我们的未来，可能是构建智能系统的最佳方法
- AI包含广泛的功能，在本次课程中，主要讲述视觉应用方面
- 构建AI应用时，可能会遇到许多挑战
- OpenVINO是Intel提供构建AI应用的工具套件，
  - 具有开源版本、免费、易使用
  - 提供多种资源帮助使用



## 2 什么是计算机视觉？如何使用计算机来处理视频？

### 2.1 图像的基本概念

- 视频中的大数据：据统计每天全球会有5亿人观看至少1部网络视频，而80%的互联网流量被视频占据，视频中包含了大量的数据，它是由一系列连续的图像构成的，只要这些图像的移动速度足够快，便可以让我们产生物体连续运动的错觉
- 图像的表示：每个图像由像素构成，每个像素都有一个表示其强度的值。在灰度图像中，每个像素由0~255表示，255表示白色，0表示黑色。在彩色图像中，像素由三个基本色RBG值组合而成，在图像中，像素的急剧变化可以表示为物体的边缘。

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/edge of object.png"
         alt="Edge of object"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

### 2.2 图像处理 

- 模糊：把每个像素的值，替换为周围8个像素的平均值，并对整张图像重复进行该操作，得到更模糊的图像

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/average of 8 neighbors.png"
         alt="average of 8 neighbors"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

- 锐化：反向扩大每个像素点与周围像素点的差异，得到更锐利的图像，我们将此操作称之为锐化。

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/blur&sharpen.png"
           alt="blur&sharpen"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

  继续进行锐化，图像将仅保留像素值的显著差异，只能看到图像中物体的边缘，可用于检测图像的角、边缘、线等

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/edge_image.png"
         alt="edge_image"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

### 2.3 OpenCV简介

- 概述：OpenCV是一款面向计算机视觉功能的开源库，它是计算机视觉领域最常用的工具库，使用C、C++、Python等多种编程语言编写，可在Intel硬件上加速，这意味着它使用Intel芯片上特定的加速单元来加快视觉程序的运行速度，并兼容多种操作系统和平台，具有计算机视觉所需的大多数功能
- 基本功能：图像的旋转、缩放、调整、过滤，查找边缘或其他特征等操作
- 高级功能：面部检测、特征识别等

### 2.4 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_2.png"
         alt="summary_2"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

- 视频占互联网流量的80%
- 视频是一系列连续的图像，这些图像的移动速度足够快，让我们的眼睛看到了平滑连续的视觉效果
- 图像是多个像素组成的阵列，每个像素均具有强度级或由RGB值共同组成
- 可以操控像素来模糊、锐化图像或执行其他任务
- 可以检测图像中的特征，查找图像中的边缘、线、角，并由此查找由线、圆形和边缘构成的真实图像
- OpenCV是一款用于加速计算机视觉的Intel软件，它是视觉领域最常用的库，并可以轻松地在Intel硬件上加速
- OpenCV已包含在OpenVINO中



## 3 如何加速视频处理进程

### 3.1 视频的数据量

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/Data volume of video.png"
         alt="Data volume of video"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


- 1帧包括`1920*1080`个像素点，
- 每个像素由RGB组成，1帧图像的大小为`6.2MB`
- 假设每秒25帧，每秒需要`155MB`的数据存储，1分钟的视频需要存储`9.3GB`的数据
- 使用视频压缩技术，如YouTube视频，1分钟仅需要`71.9MB`的数据，一般来说，为了保证网络的数据流量通畅，视频在网络上传输的版本都是经过视频压缩的，一个一分钟的视频文件大小应该在`100MB`以下

### 3.2 视频压缩技术

- 空间冗余：例如图像中几张照片中相同天空区域的矩形位置，所有像素都是几乎相同的颜色，只需要存储矩形中所有像素的颜色平均值，在显示的时候，把这个颜色应用于整个矩形中的每一个像素

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/spatial redundancy.png"
         alt="spatial redundancy"
         style="zoom:0.6"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


- 时间冗余：视频中截取的几帧，图像局部区域是一样的，但在屏幕中的位置不断变化，因此基本上不需要重复存储这些像素。可以只存储第一张图像该区域的像素值，接下来的几张图像的矩形区域可以重复直接使用第一张图片存储的像素值。

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/temporal redundancy.png"
         alt="temporal redundancy"
         style="zoom:0.6"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


- 帧值处理：假设有一个新帧图像，记作`I`帧

  - `I`帧：包含新信息，因此保留所有像素数据

  - `P`帧：在两个`I`帧之间存在`P`帧，记录两帧之间的差异，数据量通常只有`I`帧的1/2
  - `B`帧：在`I`帧和`P`帧之间是`B`帧，`B`帧是帧与帧之间的插值，数据只有`I`帧的1/4，它们之间的变化可以自动生成

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/I_P_B.png"
         alt="I_P_B"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

### 3.3 编解码器与视频加速处理

- 视频传输流程：先编码，后解码

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/video transmission process.png"
         alt="video transmission process"
         style="zoom:0.6"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


- 视频文件：是一个可以容纳其他文件的文件容器，例如mp4文件包括：
  - 带显示的视频流：h.264
  - 带播放的视频：经过编码的mp3
  - 元数据：比特率、分辨率、编解码器等
- 视频处理任务：将海量的数据存储在大型的缓冲区中，并逐帧进行处理，对两帧进行对比，查看发生的变化
- 硬件：Intel CPU能够处理编解码任务，使用Intel Quick Sync Video Technology，快速视频同步技术；Intel核心显卡包括两大核心模块，EU和QSVT，EU用于处理图像视频渲染，QSVT包括加速视频处理、解码、编码等等，集成GPU可以在睿频模式下运行

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/Intel integrated GPU.png"
         alt="Intel integrated GPU"
         style="zoom:0.6"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>



- 软件：驱动程序在集成GPU的上层，在驱动程序之上是VAAPI-Libva，上层封装了Media-SDK，提供C++/Python语言的API接口，可使用OpenCV、FFMPEG、Gstreamer直接访问该API，OpenVINO包含了Media-SDK

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/Media-SDK.png"
         alt="Media-SDK"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


### 3.4 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_3.png"
         alt="summary_3"
         style="zoom:0.7"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

- 视频流传输是一项繁重的任务，数据量非常大
- 视频压缩利用图像和不同帧的冗余性，通过较少的数据表示相同数据的信息
- 介绍编解码器、视频容器文件等内容
- 通过软件在CPU上执行视频处理，但Intel集成GPU也能提供专业硬件单元用于视频处理
- Media-SDK可以利用Intel快速视频同步技术进行视频处理包括编码、解码以及后处理等等
- 可以通过OpenCV、FFMPEG、Gstreamer使用Media-SDK
- Media-SDK是OpenVINO的一部分



## 4 如何给视觉应用中的神经网络加速

### 4.1 视觉图像识别的应用

- 特征：通过图像锐化，得到图像边缘特征，观察特定像素的排列，这些角、线、圆等组成元素称为特征

- 猫的检测：检测对象是否有4条腿、尾巴、颜色、大小等，将所有输入特征放在一个函数中，如果组合正确，就可以判断是猫

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/cat_1.png"
           alt="cat_1"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>
  
  
  同时，为了让模型能检测出更多的猫，泛化性更好，需要对每个特征赋予一定的权重，即每个特征值乘以一个权重，这些相乘的结果加上经过转换之后输出，输出结果等于1则是猫，等于0则不是猫。
  
  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/cat_2.png"
           alt="cat_2"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>
  

  而想要检测出更复杂的对象，需要更多的隐藏层，对于神经网络来说层数越多则代表包含的特征越多，若是只有一层则可能包含的特征比较少，不能准确地进行判断，所以我们需要多层结构的神经网络。并且函数与特征之间需要非线性的关系
  
  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/cat_3.png"
           alt="cat_3"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>
  
  
  再进一步，所谓的特征提取器也是对图像进行数学的运算，因此也可以转换成神经网络结构，添加到主函数中。
  
  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/cat_4.png"
           alt="cat_4"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

### 4.2 神经网络模型构建

- 前向操作，进行分类，图像和网络相乘，计算误差
- 反向操作，更改神经网络的权重，将结果错误率降到最低
- 反复上述操作，获取特定权重的神经网络，进行迭代训练

### 4.3 模型类别

在图像识别、语音识别领域，使用很多模型进行处理，比如：

- 分类模型：图像包含特定对象的概率
- 检测模型：检测图像中目标物体的边界框
- 分割模型：对图像中的物体（每个像素）进行分类，并判断是否为特定对象

### 4.4 DLDT简介

- DLDT：深度学习部署工具套件（Deep Learning Deployment Toolkit）是属于OpenVINO的核心组件，包含构建AI的解决方案、可随时使用的示例、程序和模型下载器等
- 运行方式：
  1. 使用预训练模型（可支持TensorFlow、Caffe、Mxnet、ONNX）
  2. 使用模型优化器转换成中间表示成中间表示IR（更改权重格式、优化拓扑等）
  3. 使用推理引擎读取IR文件，推理引擎的代码可重复使用，只需要进行非常小的修改，可以在Intel多种硬件上进行推理

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/DLDT.png"
         alt="DLDT"
         style="zoom:0.7"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

### 4.5 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_4.png"
         alt="summary_4"
         style="zoom:0.6"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


- 基于深度学习的神经网络是一种各种视觉相关任务的可靠方法
- 为了获得可以正常运行的网络模型，在训练流程中处理了大量的数据
- 推理是网络的正向路径，输出结果，计算误差，并执行反向路径，更新权重
- 深度学习模型可用于分类、检测、分割和其他任务
- Intel平台可执行神经网络，并提供卓越的性能
- DLDT是一款用于加速深度学习推理的Intel软件工具，是OpenVINO的组成部分



## 5 视频分析处理的完整流程

### 5.1 视频分析工作流程

1. 解码：解码多个视频流，每个视频流具有不同的分辨率和格式，解码的视频流可以通过摄像头，RTSP，视频文件等获取
2. 预处理：通过锐化、亮度调整、可缩放图像、裁剪图像中感兴趣的区域，选择跳过帧或尝试推理所有帧等操作
3. 推理：使用深度学习模型进行推理，如进行对象检测、分类对象
4. 发送处理：可在被检测对象周围绘制边界框
5. 编码：压缩视频，用于发送或存储视频

### 5.2 各种组件在流程中的应用

- `Media-SDK`用于处理视频编解码和图像预处理

- `DLDT`基于深度学习的推理加速

- `OpenCV`基本上能完成整个流程

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/application of components in the process.png"
           alt="application of components in the process"
           style="zoom:0.7"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

### 5.3 OpenVINO的架构

- 支持多个Intel架构基础平台

- 使用OpenCV处理计算机视觉

- 使用Media-SDK进行视频编解码与处理

- 使用DLDT进行推理

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/Distribution of OpenVINO toolkit.png"
           alt="Distribution of OpenVINO toolkit"
           style="zoom:0.7"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

### 5.4 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_5.png"
         alt="summary_5"
         style="zoom:0.7"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

- 视频分析：视频处理、计算机视觉和AI推理
- 视频分析流程是多种视觉应用最常用的工具负载
- 视频分析流程包括多项操作，但是消耗资源最大的操作在每一帧上都需要执行
- OpenVINO具有构建视频分析流程和AI应用的所需要的软件工具
- OpenVINO支持多个Intel平台和多种操作系统，免费开放使用，拥有所有必要的工具



## 6 OpenVINO的示例演示

### 6.1 OpenVINO示例

- 交互式人脸检测：netron查看深度学习模型，通过一个摄像头获取人脸，使用脸部检测模型，年龄和性别检测模型、头部位置和情绪检测模型、面部特征检测模型等
- 多通道人脸检测：通过视频流进行人脸检测
- 重新识别和跟踪：人员检测模型，绘制每个人的跟踪路线
- 道路分割：将每辆汽车进行分割，并显示标签

### 6.2 基本指令

- -i：标记的是视频流的输出源位置
- -i cam：表示摄像头输入视频
- -m：表示读入的模型文件
- -nc：表示摄像头数量
- -d：可以更改CPU推理和集成显卡推理

### 6.3 基本文件格式

- 模型优化器会生成模型的中间表示 (IR) 文件，可以使用推理引擎对其进行读取、加载和推理
- 中间表示包括一个描述网络拓扑的`.xml` 文件和一个包含权重数据的`.bin`文件
- 一般用`XML`文件作为读入模型的文件，应用程序会通过前缀寻找到相同文件目录下的`.BIN`文件自动读入

### 6.4 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_6.png"
         alt="summary_6"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>



## 7 如何使用英特尔OpenVINO工具实现从数据采集到AI产品诞生（上）

### 7.1 构建AI应用流程

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/AI application process.png"
         alt="AI application process"
         style="zoom:0.5"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>


- 描述开发人员从选择正确模型到构成系统的整个阶段

- 系统选择（Select System）：选择合适的系统后，产品可以轻松的扩展，并能够在任何银行或超市环境中安装使用，可在一个系统中部署不同的设备，比如CPU、GPU、FPGA和AI加速器

  1. CPU：OpenVINO代码是可以移植的，针对CPU编程，之后可以轻松将程序移植到其他设备，支持ATOM、CORE、XEON等系列
  2. GPU：渲染3D图形、加速推理和视频处理（编解码），支持IRIS、Discreate Graphics等系列
  3. FPGA：支持Arria10 HDDL-F
  4. AI加速器：支持MOVIDIUS、NERVANA等智能硬件，提升8~10倍加速

- 寻找模型（Model）：

  - 基于深度学习的模型执行分割、检测、分类任务等
  - 模型在另外的框架中进行训练，例如Tensorflow或者caffe

- 准备推理（Perpare Inference）：

  - 模型通常在云环境中进行训练，云环境拥有所有的计算资源
  - 但是要为推理做好准备，有时是在较小的设备上进行推理

  - 模型通常采用浮点格式，有时是在执行整数或者其他设备上运行，因此可能需要转换数据格式

- 性能指标评测（Benchmark）：用于了解模型性能，比如每秒可以执行的推理次数，可以使用多种优化技术和多种数据格式，最终选择满足性能要求的平台

- 解码能力（Decode Density）：应支持尽可能多的摄像头或者视频流，从而降低每个摄像头的成本，因此需要了解解码能力与编码能力

- 完整流程（Full Pipeline）：

  - 了解从推理、性能指标评测、编解码能力的多个流程
  - 解码、编码与推理任务是一起运行的，一起运行所得到的结果可能差强人意
  - 因此要模拟完整的工作环境负载，所有功能同时执行，使用Gstreamer进行模拟

- AI应用（AI Application）：构建软件或使用OpenVINO将视频分析流程和推理整合到现有的应用中

### 7.2 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_7.png"
         alt="summary_7"
         style="zoom:0.7"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

- OpenVINO提供了构建AI应用的所有工具：获取一个深度学习模型，对视频分析流程中的所有指标进行性能评测，最后构建一个AI应用
- Intel有多种平台可供选择，包括CPU、集成GPU、基于Movidius的VPU和FPGA
- OpenVINO支持异构系统



## 8 如何使用英特尔OpenVINO工具实现从数据采集到AI产品诞生（下）

### 8.1 获得模型（Model）

- 模型下载器（Model Downloader）

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/Model Downloader.png"
           alt="Model Downloader"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

- 训练（Train）模型：

  - 收集数据（Collect）：尽可能收集与推理环境相同的数据

  - 清洗数据（Prepare）：使用CV技术对这些数据进行清洗、裁剪、分离，拿到真正有用的数据

  - 图像标注（Annotate）：可以使用计算机视觉标注工具，对这些分离的数据进行信息标注，这样的数据集作为我们训练的输入数据集

  - 训练（Training）：

    <div>			<!--块级封装-->
        <center>	<!--将图片和文字居中-->
        <img src="./res/Training.png"
             alt="Training"
             style="zoom:0.5"/>
        <br>		<!--换行-->
        <!--标题-->
        </center>
    </div>

- Model Zoo：预训练模型（Pre-Trained models），训练扩展（Training extensions）支持基于自定义数据或提供的检查点进行模型训练。以复制整个训练项目，从0开始或者从设置的检查点开始，直接用自己的数据集来替换原始的数据集

### 8.2 准备推理（Perpare Inference）

- 模型优化器（Model Optimizer）：将多种类型的模型（Model）转换为IR格式的模型，将其映射到正确的库函数或内核（Map），可以使用水平或垂直融合、归一化、规范化各种技术优化模型（Optimize），支持添加或删除一个或多个神经网络层（Customize），最终得到一个优化过的精简模型

### 8.3 性能指标评测（Benchmark）

- 提供指标评测器（Benchmark App），可显示延迟、吞吐量等信息

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/Inference Transformation Model.png"
           alt="Inference Transformation Model"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

- Dev Cloud：类似于大型的沙盒，支持所有Intel芯片，提供所有的软件，远程连接设备，对工作负载进行性能测试
- 性能计算器（Performance Counters）：OpenVINO已内置，可以运行网络，查找每一层的统计数据
- WorkBench：提供直观的图形界面，支持性能测试的展示

### 8.4 解码能力（Decode Density）

- 提供监控集成显卡利用率的工具

- 提供快速入门示例

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/Media-SDK_Encode_Decode.png"
           alt="Media-SDK_Encode_Decode"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

### 8.5 完整流程（Full Pipeline）

- OpenVINO GStreamer Video Analystics（GVA）插件：包括OpenVINO Inference Elements和GStreamer Elements，用于构建视频处理流程的平台，提供分类、检测、识别、跟踪和可视化等流程
- Gstreamer可以用于视频分析
- `video1.mp4`是输入视频文件
- `decodebin`对视频进行解码
- `videoconvert`转换视频格式，为下一阶段推理做准备
- `face-detection.xml`使用脸部检测模型进行人脸检测
- `emotions-recognition.xml`用输出的结果进行情绪识别

### 8.6 AI应用（AI Application）

- 提供40个C++/Python演示示例

- 提供高级操作，例如多路视频分析、跟踪对象

- 提供简短代码片段，可以直接放入应用中

  <div>			<!--块级封装-->
      <center>	<!--将图片和文字居中-->
      <img src="./res/AI Application.png"
           alt="AI Application"
           style="zoom:0.5"/>
      <br>		<!--换行-->
      <!--标题-->
      </center>
  </div>

### 8.7 总结

<div>			<!--块级封装-->
    <center>	<!--将图片和文字居中-->
    <img src="./res/summary_8.png"
         alt="summary_8"
         style="zoom:0.7"/>
    <br>		<!--换行-->
    <!--标题-->
    </center>
</div>

- OpenVINO是一款用于构建视频分析流程的综合分析套件
- 可以在整个流程中使用相应的工具、程序和资源：获得深度学习模型、针对推理准备模型、执行性能指标评测、查看编解码能力、模拟完整的软件产品流程、构建AI应用



## 9 课程回顾

- 第1节课：介绍了AI将改变我们生活的方方面面，视觉应用将带来机遇和商业潜力
- 第2节课：视频是互联网最常见的传输数据类型，讨论了像素，并了解大量的像素构建了图片，大量的图片构成了视频；可通过过滤图像、模糊、锐化、边缘检测的特征提取等操作，介绍了使用OpenCV能加速视觉计算处理
- 第3节课：介绍了视频压缩、冗余及视频压缩的工作原理，使用Intel集成显卡加速压缩，通过Media-SDK使用Intel快速视频同步技术加速视频处理
- 第4节课：介绍了人工智能算法、面向视觉应用的神经网络，并讨论了实时执行神经网络的复杂性，主要介绍了使用模拟化优化器和推理引擎加速视频推理
- 第5节课：介绍了视频分析流程，构建AI应用的所需步骤和落地要求，并介绍了OpenVINO的整体架构
- 第6节课：提供了DEMO演示，主要展示了交互式人脸检测、多路人脸检测、重新识别和跟踪、道路分割等示例
- 第7节课：介绍了Intel提供的异构平台，并介绍了各种硬件产品，包括CPU、GPU、FPGA和AI加速器等，学习OpenVINO构建完整AI应用流程
- 第8节课：详细讲解了整个流程，并介绍了可供开发人员使用的工具、程序和资源



## 10 任务总结

  本次任务，介绍了人工智能算法、面向视觉应用的神经网络、实时执行神经网络的复杂性，并介绍了OpenVINO的推理引擎加速视频推理：

1. OpenVINO是Intel提供构建AI应用的工具套件，具有开源版本、免费、易使用，提供多种资源帮助使用
2. OpenCV是一款用于加速计算机视觉的Intel软件，是视觉领域最常用的库，并可以轻松地在Intel硬件上加速
3. Media-SDK调用Intel快速视频同步技术加速视频处理
4. DLDT是一款用于加速深度学习推理的Intel软件工具，是OpenVINO的组成部分
5. 视频分析流程包括解码、预处理、推理、发送处理和编码等环节
6. IR文件：模型优化器生成网络的中间表示，包括xml文件（网络拓扑）和bin文件（经过训练的数据文件，包含权重和偏差）
7. OpenVINO具有构建视频分析流程和AI应用的所需要的软件工具
8. 演示交互式人脸检测、多路人脸检测、重新识别和跟踪、道路分割等示例
9. 介绍构建AI应用的完整流程，以及用到的所有工具
10. Intel® DeCloud的使用流程：网页登陆--->链接至DevCloud服务器--->推理任务部署--->返回推理结果