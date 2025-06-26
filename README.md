# # PRISM GPU 预补充知识

## 图形学  （一个月）

### 图形学课程    

1、图形学最好的补充知识的课程是通过《[GAMES101](https://www.bilibili.com/video/BV1X7411F744/?spm_id_from=333.337.search-card.all.click&vd_source=789ca485118ffcb40f218817d111e55e)》但是这门课程对于大一大二的本科生可能具有不小的难度，当然如果你是卷王除外。如果你没有学过线性代数或者线性代数掌握的并不深刻，那么我十分建议你的前导课程从《[线性代数](https://www.bilibili.com/video/av6731067/?p=4&vd_source=789ca485118ffcb40f218817d111e55e)》开始。

2、GAMES101的学习建议是光线追踪之前的所有章节，学习方式是每天一章，并且当天将作业做一遍，如果一天做不完，那么就做完作业在开始下一章节，关于作业在哪里我就不在这里指定了，在GitHub之类的平台上由很多仓库。那么如果你觉得你并不是很理解课程以及作业，那么我建议你从虎书上找答案《[Fundamentals-Of-Computer-Graphics-5th-CN](./eBook/Fundamentals_of_Computer_Graphics.pdf)》，当你做完光栅化以及光栅化之前的作业你就可以的到一个Soft Shader 软光栅器了。

### 备注：

当然这个课程很好但是还需要进行一些详细的补充，比如MVP变换之后的裁剪问题，以及透视投影矫正的问题，以及光栅化的算法之类的并没有很详细的讲述出来，所以这里增加一些备注。

（我是看过就贴在上面了，有更好的欢迎PR）

裁剪 [齐次空间裁剪](https://zhuanlan.zhihu.com/p/162190576) [观察空间到裁剪空间的投影矩阵推导](https://jdreamheart.com/wiki/knowledge/math/model_2_clip_projection_matrix/) 等等。

透视投影矫正 [lowk persp interp techrep](./eBook/lowk_persp_interp_techrep.pdf) 这篇论文足够。

## 图形API（以OpenGL为例）（2周）

### API教程

1、学习API，我的建议是按照教程 [LearnOpenGL-CN](https://learnopengl-cn.github.io/) 走一遍，这个教程是英文的翻译版，有句子读起来可能比较坳口，我的建议是在了，linux上做，并且自己配置GLAD GLM等框架和库，通过自己配置框架和库 可以了解那部分是是API的工作那部分是库的工作。时间紧迫的话只需要做入门章节和光照章节即可，时间充分还可以继续做高级OpenGL和高级光照，只不过这些只是短时间内我们还用不到，完成这一部分，你会有很有意思的成果，然后在你打游戏的时候你看到的就不只是炫酷的特效了，而是特效的顶点，纹理，和他调用的API。

### 备注

这部分的工作主要是让你知道什么是API，到这一步你基本上已经能了解一个游戏从你打开到你关闭他的每一步背后的原理了，貌似这和GPU没有什么关系，这主要的原因是因为GPU不向CPU（主要给搞体系结构的人举的例子）一样有一个完整的tool chian和架构给你准备好了让你使用，你需要先了解上层。当然还有一点就是GPU的这些API是很接近物理层的，尤其是你写过CUDA的话。

## 初识驱动 （1.5个月）

### Windows图形框架 WDDM

这里之所以用这个举例子是因为微软的驱动示例库里面有一个WDDM display only的框架，基于这个框架你可以比较轻松的把他该放到你自己的设备上，这里推荐我之前做过的实践项目([PrismGPU](https://github.com/PrismGPU/PrismGPU)) 这个工作主要是首先你需要熟悉WDDM框架 其次需要你自行的在QEMU上实现一个虚拟的{PCIE的伪硬件设备，作为你的Display设备，其次需要你会使用WInDbg工具进行内核驱动程序的调试。这个工作主要是实现了一个KMD，但是这就足够啦，因为通过上面的了解你基本上已经知道UMD（也就是API的算法实现）的作用是什么了，那么再加上KMD进行一些内核工作的处理以及维护显存，你现在基本上已经知道了一个游戏从你打开到你关闭他的所有细节了。

### 备注：

到这里可能你觉得GPU就这么简单，不过我认为你没有这样的想法是最好的，因你现在连最简单的Fix Function的GPU都还没有写出来，你现在距离写出来一块Fix Function还差Mesa图形库移植，Linux DRM框架的实现，Fix Function的物理实现（这应该算是最简单的了）。并且即时是Fix Function GPU还有Video En/Decode视频编解码器的实现呢。更何况现代GPU都是可编程的还需要设计一套自己的SIMD架构和GLSL编译器。所以任重道远。

欢迎所有完成以上工作的同学加入我们。

邮箱：asdcdqwe@163.com

WeiChat：16795305505
