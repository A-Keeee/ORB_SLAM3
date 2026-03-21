# ORB-SLAM3

### V1.0, 2021年12月22日
**作者:** Carlos Campos, Richard Elvira, Juan J. Gómez Rodríguez, [José M. M. Montiel](http://webdiis.unizar.es/~josemari/), [Juan D. Tardos](http://webdiis.unizar.es/~jdtardos/).

[更新日志(Changelog)](https://github.com/UZ-SLAMLab/ORB_SLAM3/blob/master/Changelog.md) 中描述了每个版本的功能特​​性。

ORB-SLAM3 是第一个能够使用**单目、双目和 RGB-D** 相机（支持**针孔和鱼眼**相机模型）进行**纯视觉、视觉-惯性 (Visual-Inertial) 及多地图 (Multi-Map) SLAM** 的实时 SLAM 库。在所有传感器配置下，ORB-SLAM3 与文献中现有的最优秀系统一样鲁棒，且精度显著提高。

我们提供了使用带有或不带 IMU 的双目/单目相机在 [EuRoC 数据集](http://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets) 上运行 ORB-SLAM3 的示例，以及使用带有或不带 IMU 的鱼眼双目/单目相机在 [TUM-VI 数据集](https://vision.in.tum.de/data/datasets/visual-inertial-dataset) 上运行的示例。部分示例运行的视频可以在 [ORB-SLAM3 频道](https://www.youtube.com/channel/UCXVt-kXG6T95Z4tVaYlU80Q) 中找到。

本软件基于由 [Raul Mur-Artal](http://webdiis.unizar.es/~raulmur/), [Juan D. Tardos](http://webdiis.unizar.es/~jdtardos/), [J. M. M. Montiel](http://webdiis.unizar.es/~josemari/) 和 [Dorian Galvez-Lopez](http://doriangalvez.com/) ([DBoW2](https://github.com/dorian3d/DBoW2)) 开发的 [ORB-SLAM2](https://github.com/raulmur/ORB_SLAM2)。

<a href="https://youtu.be/HyLNq-98LRo" target="_blank"><img src="https://img.youtube.com/vi/HyLNq-98LRo/0.jpg" 
alt="ORB-SLAM3" width="240" height="180" border="10" /></a>

### 相关出版物:

[ORB-SLAM3] Carlos Campos, Richard Elvira, Juan J. Gómez Rodríguez, José M. M. Montiel and Juan D. Tardós, **ORB-SLAM3: An Accurate Open-Source Library for Visual, Visual-Inertial and Multi-Map SLAM**, *IEEE Transactions on Robotics 37(6):1874-1890, Dec. 2021*. **[PDF](https://arxiv.org/abs/2007.11898)**.

[IMU-Initialization] Carlos Campos, J. M. M. Montiel and Juan D. Tardós, **Inertial-Only Optimization for Visual-Inertial Initialization**, *ICRA 2020*. **[PDF](https://arxiv.org/pdf/2003.05766.pdf)**

[ORBSLAM-Atlas] Richard Elvira, J. M. M. Montiel and Juan D. Tardós, **ORBSLAM-Atlas: a robust and accurate multi-map system**, *IROS 2019*. **[PDF](https://arxiv.org/pdf/1908.11585.pdf)**.

[ORBSLAM-VI] Raúl Mur-Artal, and Juan D. Tardós, **Visual-inertial monocular SLAM with map reuse**, IEEE Robotics and Automation Letters, vol. 2 no. 2, pp. 796-803, 2017. **[PDF](https://arxiv.org/pdf/1610.05949.pdf)**. 

[Stereo and RGB-D] Raúl Mur-Artal and Juan D. Tardós. **ORB-SLAM2: an Open-Source SLAM System for Monocular, Stereo and RGB-D Cameras**. *IEEE Transactions on Robotics,* vol. 33, no. 5, pp. 1255-1262, 2017. **[PDF](https://arxiv.org/pdf/1610.06475.pdf)**.

[Monocular] Raúl Mur-Artal, José M. M. Montiel and Juan D. Tardós. **ORB-SLAM: A Versatile and Accurate Monocular SLAM System**. *IEEE Transactions on Robotics,* vol. 31, no. 5, pp. 1147-1163, 2015. (**2015 IEEE Transactions on Robotics Best Paper Award**). **[PDF](https://arxiv.org/pdf/1502.00956.pdf)**.

[DBoW2 Place Recognition] Dorian Gálvez-López and Juan D. Tardós. **Bags of Binary Words for Fast Place Recognition in Image Sequences**. *IEEE Transactions on Robotics,* vol. 28, no. 5, pp. 1188-1197, 2012. **[PDF](http://doriangalvez.com/php/dl.php?dlp=GalvezTRO12.pdf)**

# 1. 许可证 (License)

ORB-SLAM3 在 [GPLv3 许可证](https://github.com/UZ-SLAMLab/ORB_SLAM3/LICENSE) 下发布。关于所有代码/库依赖项（及相关许可证）的列表，请参阅 [Dependencies.md](https://github.com/UZ-SLAMLab/ORB_SLAM3/blob/master/Dependencies.md)。

对于用于商业目的的 ORB-SLAM3 闭源版本，请联系作者：orbslam (at) unizar (dot) es。

如果您在学术工作中使用 ORB-SLAM3，请引用：
  
    @article{ORBSLAM3_TRO,
      title={{ORB-SLAM3}: An Accurate Open-Source Library for Visual, Visual-Inertial 
               and Multi-Map {SLAM}},
      author={Campos, Carlos AND Elvira, Richard AND G\´omez, Juan J. AND Montiel, 
              Jos\'e M. M. AND Tard\'os, Juan D.},
      journal={IEEE Transactions on Robotics}, 
      volume={37},
      number={6},
      pages={1874-1890},
      year={2021}
     }

# 2. 依赖项 (Prerequisites)
我们已经在 **Ubuntu 16.04** 和 **18.04** 中测试了该库，但它应该也很容易在其他平台上编译。一台性能强大的计算机（例如 i7 处理器）将确保实时性能并提供更稳定和准确的运行结果。

## C++11 或 C++0x 编译器
我们使用了 C++11 中的新线程和 chrono 功能。

## Pangolin
我们使用 [Pangolin](https://github.com/stevenlovegrove/Pangolin) 用于可视化和用户界面。下载和安装说明可参考：https://github.com/stevenlovegrove/Pangolin。

## OpenCV
我们使用 [OpenCV](http://opencv.org) 处理图像和提取特征。下载和安装说明可参考：http://opencv.org。**至少需要 3.0 版本。已在 OpenCV 3.2.0 和 4.4.0 版本测试**。

## Eigen3
g2o所需（见下文）。下载和安装说明可参考：http://eigen.tuxfamily.org。**至少需要 3.1.0 版本**。

## DBoW2 和 g2o（包含在 Thirdparty 文件夹中）
我们使用修改版的 [DBoW2](https://github.com/dorian3d/DBoW2) 库执行位置识别，使用 [g2o](https://github.com/RainerKuemmerle/g2o) 库执行非线性优化。这两个修改过的库（均为 BSD 许可协议）都已经包含在 *Thirdparty* 文件夹中。

## Python
用于计算轨迹与真实轨迹 (Ground Truth) 的对齐误差。**需要 Numpy 模块**。

* (win) http://www.python.org/downloads/windows
* (deb) `sudo apt install python-dev` (或 `python3-dev`)
* (mac) 预装于 OS X

## ROS (可选)
我们提供了一些示例来处理基于 ROS 的单目、单目-惯性、双目、双目-惯性或 RGB-D 传感器的输入。编译这些示例是可选的。这些已经在 Ubuntu 18.04 下的 ROS Melodic 中测试通过。

# 3. 编译 ORB-SLAM3 库和示例

克隆项目仓库：
```
git clone https://github.com/UZ-SLAMLab/ORB_SLAM3.git ORB_SLAM3
```

我们提供了一个脚本 `build.sh` 来编译 *Thirdparty* 中的第三方库和 *ORB-SLAM3*。请确保您已预先安装了所有必需的依赖项（参阅第2节）。依次执行：
```
cd ORB_SLAM3
chmod +x build.sh
./build.sh
```

这将在 *lib* 文件夹中生成 **libORB_SLAM3.so** 共享库，在 *Examples* 文件夹中生成对应示例的可执行文件。

# 4. 使用您自己的相机运行 ORB-SLAM3

`Examples` 目录中包含了好几个示例程序和标定文件，可以使用 Intel Realsense T265 和 D435i 以及所有传感器配置来运行 ORB-SLAM3。若要使用您自己的相机，请遵照以下步骤：

1. 按照 `Calibration_Tutorial.pdf` 中的教程校准您的相机，并编写您的标定文件 `your_camera.yaml`。

2. 修改提供的示例程序之一以适应您的特定相机型号，然后编译它。

3. 使用 USB3 或适当的接口将相机连接到你的计算机。

4. 运行 ORB-SLAM3。例如，对于我们的 D435i 相机，我们将执行：

```
./Examples/Stereo-Inertial/stereo_inertial_realsense_D435i Vocabulary/ORBvoc.txt ./Examples/Stereo-Inertial/RealSense_D435i.yaml
```

# 5. EuRoC 数据集示例
[EuRoC 数据集](http://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets) 是由两个针孔相机和一个惯性传感器录制的。我们提供了一个脚本来处理涵盖所有传感器配置的 EuRoC 序列集。

1. 从 http://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets 下载（ASL 格式的）数据集序列。

2. 打开位于项目根目录下的 "euroc_examples.sh" 脚本。更改 **pathDatasetEuroc** 变量使其指向您解压数据集所在的目录。

3. 执行以下脚本以通过所有传感器配置处理所有序列：
```
./euroc_examples
```

## 评估
EuRoC 中的每段序列在其 IMU 的本体坐标系中给出了真实的 Ground Truth（真值）。由于仅使用纯视觉估计会输出以左手相机为中心的轨迹坐标系，因此我们在 "evaluation" 文件夹中提供了将真值转换至左侧相机坐标系的基准。如果是视觉-惯性轨迹将直接使用来自数据集本体的真值。

执行以下脚本以处理序列并计算 RMS ATE（绝对轨迹误差均方根）：
```
./euroc_eval_examples
```

# 6. TUM-VI 数据集示例
[TUM-VI 数据集](https://vision.in.tum.de/data/datasets/visual-inertial-dataset) 是由两个鱼眼相机和一个惯性传感器录制的。

1. 从 https://vision.in.tum.de/data/datasets/visual-inertial-dataset 下载数据序列并将其解压。

2. 打开项目根目录下的 "tum_vi_examples.sh" 脚本。更改 **pathDatasetTUM_VI** 变量以指向存放解压数据的目录。

3. 执行以下脚本以通过所有的传感器配置处理各段序列：
```
./tum_vi_examples
```

## 评估
对于 TUM-VI，基准真值仅在序列起点和终点所在的房间内提供。因此误差评估主要衡量位于序列终点处的漂移大小。

执行以下脚本来处理数据序列并计算 RMS ATE：
```
./tum_vi_eval_examples
```

# 7. ROS 示例下的运行

### 构建单目、单目-惯性、双目、双目-惯性以及 RGB-D 的 ROS 节点
已经在 Ubuntu 18.04 的 ROS Melodic 下进行过测试。

1. 将包含 *Examples/ROS/ORB_SLAM3* 的路径添加到 `ROS_PACKAGE_PATH` 环境变量中。打开 .bashrc 文件：
  ```
  gedit ~/.bashrc
  ```
然后再最后添加下面这行代码（请将 PATH 替换为拉取存放 ORB_SLAM3 的实际路径）：

  ```
  export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:PATH/ORB_SLAM3/Examples/ROS
  ```
  
2. 运行 `build_ros.sh` 脚本:

  ```
  chmod +x build_ros.sh
  ./build_ros.sh
  ```
  
### 运行单目节点 (Monocular Node)
对于从主题 `/camera/image_raw` 接收单目输入的场景，运行节点 ORB_SLAM3/Mono。您必须为其提供词典文件和设置(yaml)文件。详见上述。

  ```
  rosrun ORB_SLAM3 Mono PATH_TO_VOCABULARY PATH_TO_SETTINGS_FILE
  ```

### 运行单目-惯性节点 (Monocular-Inertial Node)
对于从主题 `/camera/image_raw` 接收单目图像且从 `/imu` 接收惯性数据的输入场景，请运行 ORB_SLAM3/Mono_Inertial 节点。将可选的第三个参数设置为 true 会对图像执行 CLAHE 均衡（主要针对 TUM-VI 数据集使用）。

  ```
  rosrun ORB_SLAM3 Mono_Inertial PATH_TO_VOCABULARY PATH_TO_SETTINGS_FILE [EQUALIZATION]
  ```

### 运行双目节点 (Stereo Node)
若需接收来自 `/camera/left/image_raw` 及 `/camera/right/image_raw` 的左右目图像，运行 ORB_SLAM3/Stereo 节点。依然需要准备词典和配置设置文件。针对针孔相机模型，如果**提供了校正矩阵**（可参考 Examples/Stereo/EuRoC.yaml 里的写入格式），节点会在在线阶段尝试校正图像，**否则您必须提供已校正完毕的输入图像**。对于鱼眼相机模型则不需要重新校正，原生运行即为有效状态：

  ```
  rosrun ORB_SLAM3 Stereo PATH_TO_VOCABULARY PATH_TO_SETTINGS_FILE ONLINE_RECTIFICATION
  ```

### 运行双目-惯性节点 (Stereo-Inertial Node)
如果是接收来自 `/camera/left/image_raw` 、 `/camera/right/image_raw` 双目及 `/imu` 的惯性组合输入，请运行 ORB_SLAM3/Stereo_Inertial 节点。您需要提供词典文件以及设置文件。如与双目类似的情况被涉及到，还请加上校正矩阵的相关参数：

  ```
  rosrun ORB_SLAM3 Stereo_Inertial PATH_TO_VOCABULARY PATH_TO_SETTINGS_FILE ONLINE_RECTIFICATION [EQUALIZATION]
  ```
  
### 运行 RGB-D 节点 (RGB_D Node)
若是接收来自 `/camera/rgb/image_raw` 和 `/camera/depth_registered/image_raw` 的 RGB-D 传感器关联输入，请运行节点 ORB_SLAM3/RGBD。您需要为其提供词典文件及相应的配置文件。参考上方 RGB-D 相关用例。

  ```
  rosrun ORB_SLAM3 RGBD PATH_TO_VOCABULARY PATH_TO_SETTINGS_FILE
  ```

**运行 ROS demo 示例：** 下载来自 EuRoC 数据集（http://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets） 的 rosbag 包 (例如：V1_02_medium.bag)。在终端中打开 3 个选项卡(tab)，并在每个选项卡中分别为双目-惯性(Stereo-Inertial)配置执行以下命令：
  ```
  roscore
  ```
  
  ```
  rosrun ORB_SLAM3 Stereo_Inertial Vocabulary/ORBvoc.txt Examples/Stereo-Inertial/EuRoC.yaml true
  ```
  
  ```
  rosbag play --pause V1_02_medium.bag /cam0/image_raw:=/camera/left/image_raw /cam1/image_raw:=/camera/right/image_raw /imu0:=/imu
  ```
  
一旦 ORB-SLAM3 完成词典加载工作，请在 rosbag 选项卡的窗口内按下空格键。

**备注:** 针对 TUM-VI 数据集的 rosbag 在加载时由于分块组(chunk)的尺寸限制可能会发生异常。一个可能的解决方式是用默认 chunk 块大小进行重包(rebag)处理，例如：
  ```
  rosrun rosbag fastrebag.py dataset-room1_512_16.bag dataset-room1_512_16_small_chunks.bag
  ```

# 8. 运行时长分析
位于 `include\Config.h` 的标志变量可用于激活时间测量。这要求您取消注释该文件里这一行代码 `#define REGISTER_TIMES`。从而获知执行用例的时间分析表现（其不仅会在终端输出反馈，同时还会生成写回到本地对应目录名为 `ExecTimeMean.txt` 的文本记录之中）。

# 9. 校准 (Calibration)
在给出的 `Calibration_Tutorial.pdf` （校准教程文件）中您可以查阅到视觉-惯性校准指引、以及对有效的配置文件相关参数详情的详尽指导说明。
