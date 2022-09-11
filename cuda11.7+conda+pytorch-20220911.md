# windows平台下，深度学习环境配置

&emsp; 最近在写毕业论文，会用到一些之前看到的论文、博客、书本的内容；系统的整理一下，以防忘记。本人的研究方向主要是计算机视觉中的目标跟踪问题，在当前的研究趋势中，DL的方法占据了绝对的主流，虽然我认为correlation-filter的方法更加的优雅、简洁，但是在大量的数据集上表现的还是有些局限性。正所谓，工欲善其事，必先利其器；在学习更深入的理论知识之前，能够先搭建好基础实验环境，跑一些简单的demo还是比较容易获得成就感的。  
&ensp;CSDN、知乎等平台有很多介绍如何在windows系统上配置深度学习开发环境的，但是大多不太系统，需要同时在多个博客之间来回考量，本文简要介绍一下cuda+conda+pytorch的安装过程中需要主要的事情，希望能够使读者少踩一些坑，毕竟装环境这一步就可能劝退很多人。

## cuda安装  

&ensp;cuda是由NVIDIA开发的一个基于GPU的计算平台，在DL中大多训练都是在GPU的加持下进行的。在安装之前，先在NVIDIA设置中对显卡的驱动程序进行更新，之后根据驱动程序的版本选择合适的cuda toolkit进行安装，这里可以参考[驱动与cuda对应关系]( https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html)。**这里需要注意的是，RTX30系列显卡的算力是8.X，只能安装cuda11系列，不能安装cuda10系列**，这里参考[显卡与算力](https://developer.nvidia.com/cuda-gpus#compute)。
&emsp;这里以GTX1050Ti显卡为例，驱动版本为511.69，根据[驱动与cuda对应关系]( https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html)，选择cuda11.6安装。当前最新版本为cuda11.7，可以在[cudatoolkit history](https://developer.nvidia.com/cuda-toolkit-archive)中下载之前的版本。在具体安装时，可以选择自定义安装，在驱动程序组件中仅选择安装CUDA。安装成功后，应该可以在系统环境变量中，找到CUDA项。![显卡驱动与cudatoolkit对应关系]( https://raw.githubusercontent.com/kblittle/blog/main/img/cudatoolkit-driver-version-20220911.png)
&emsp;安装完cudatoolkit之后，还需要安装cudnn，这里需要注册个[账号](https://developer.nvidia.com/rdp/cudnn-download)，之后[下载](https://developer.nvidia.com/rdp/cudnn-archive)与上一步安装的cudatoolkit版本对应的cudnn。解压之后，将cudnn中的bin\include\lib文件夹复制到cudatoolkit的NVIDIA GPU Computing Toolkit文件夹中，覆盖原来的。
&emsp;到这里cuda就安装好了，打开cmd，输入  

      nvcc --version
      nvidia-smi
&emsp;查看是否安装成功

## conda安装
&emsp;python是深度学习中常用的一种计算机语言，在实际算法中会调用到很多不同版本的包。[conda](https://www.anaconda.com/)是一个简单易用的python环境管理软件，其安装较简单。

参考：
[1]https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#install-windows
[2]https://blog.csdn.net/m0_37605642/article/details/98854753

