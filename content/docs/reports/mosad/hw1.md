# **现代操作系统应用开发 作业1**

### 姓名：邵震东

### 学号：19335172

## **一、安装配置 macOS 和 Xcode**

本次实验使用 MacBook Air on Apple Silicon 完成，系统版本为 macOS Big Sur 11.5.2，Xcode 版本为 12.5.1. 

## **二、熟悉 macOS 按键操作**

macOS 拷贝、粘贴等操作使用 ⌘(command) 按键代替 Windows 中的 ctrl 键，切换中英文输入法则使用 caps lock 按键或 fn 按键. 

## **三、编译运行第一个 Xcode 项目**

根据 tutorial 中的指引，需要注意的是在 Info.plist 中不但要删除 `Main StoryBoard base file name`，同时也要删除 `Application Scene Manifest` > `Scene Configuration` > `Application Session Role` > `Item 0` > `StoryBoard Name`，才可以最终成功编译. 

我们将 tutorial 中的代码放在项目中的相应位置. 

`AppDelegate.m`

<img src="https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/mosad_hw1_AppDelegate_m.png" alt="AppDelegate_m" style="zoom:50%;" />

`ViewController.m`

<img src="https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/mosad_hw1_ViewController_m.png" alt="ViewController_m" style="zoom:50%;" />

同时，我们需要在 `AppDelegate.h` 中添加一行：

```objective-c
@property (nonatomic, strong) UIWindow * window;
```

这样，就可以成功编译了. 

可以看到 Simulator 中启动程序后屏幕变暗，Xcode 中产生输出. 

<img src="https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/mosad_hw1_Simulator.png" alt="Simulator" style="zoom:50%;" />

<img src="https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/mosad_hw1_Output.png" alt="Output" style="zoom:50%;" />

## **四、实践项目**

### **(一)、设计建模**

在这个问题中，我们令 N = 4， M = 5. 

衣服颜色有：

白色 (White)、黑色 (Black)、蓝色 (Blue) 和红色 (Red). 

裤子则有：

白色 (White)、黑色 (Black)、红色 (Red)、绿色 (Green) 和棕色 (Brown). 

设计各种搭配的得分如下：

| 上衣 / 得分 / 裤子 | 白色 (White) | 黑色 (Black) | 红色 (Red) | 绿色 (Green) | 棕色 (Brown) |
| :----------------- | :----------: | :----------: | :--------: | :----------: | :----------: |
| 白色 (White)       |      10      |      11      |     12     |      13      |      14      |
| 黑色 (Black)       |      15      |      16      |     17     |      18      |      19      |
| 蓝色 (Blue)        |      20      |      21      |     22     |      23      |      24      |
| 红色 (Red)         |      25      |      26      |     27     |      0       |      28      |

### **(二)、代码实现**

按照 `tutorial` 中给出的例子继续实现，我们首先创建 `Source.m` 和 `Source.h` 两个文件作为我们提供接口和实现类的地方. 

![Source_m](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/mosad_hw1_Source_m.png)

参考文档中给出的头文件实现，考虑到类的封装性和数据隐秘性，将成员变量改写为私有成员，并添加了对私有成员进行操作的函数，如下：

```objective-c
@interface Clothes : NSObject
{
    NSString * _color;
    NSInteger _counter;             					// 计数器，记录下衣物剩下冷却时间
}
@property (nonatomic, copy)NSString * color;	// 对 `_color` 变量的操作采用深拷贝形式

- (void)setColor: (NSString*) color;
- (NSString*) getColor;
- (NSInteger) calCounter;
- (void) setCounter;													// 置计数器为冷却时间
- (void) reduceCounter;												// 计数器 -1

@end

@interface TopClothes: Clothes

@end

@interface Trousers: Clothes

@end
```

在  `@implement` 中，应用了面向对象的多态特性，在定义 `setCounter` 时，将 `Clothes` 类中该函数定义为了无意义的虚函数，而在其两个子类中分别重写了该函数，如下：

```objective-c
// Clothes 类中的实现
- (void) setCounter
{
    return;
}

// TopClothes 类中的实现
- (void) setCounter
{
    self->_counter = 2;
}

// Trousers 类中的实现
- (void) setCounter
{
    self->_counter = 1;
}
```

根据 `tutorial` 中的例子，我们将主要代码放在了 `ViewController.m` 中实现，经验证，将其放在 `main.m` 中实现，效果是相同的. 

在实现代码中，我学会了怎样新建对象并将其放入 `NSArray` 建立的数组中，学会了使用消息传递机制在方法之间传递消息，充分体验到了将 C 语言代码嵌入 OC 中编程的方便和快捷，对 OC 编程的认识更进一步. 由于实现代码稍长，为了节减篇幅，不贴在本报告中. 

### **(三)、结果输出**

经测试，本程序具备实验要求的各种功能，得到如下输出 (其中之一)：

```
2021-09-27 17:08:03.235198+0800 HW1[53834:4004545] ZhangSan's Wardrobe!
2021-09-27 17:08:03.235287+0800 HW1[53834:4004545] 
2021-09-27 17:08:03.235412+0800 HW1[53834:4004545] Day 1
2021-09-27 17:08:03.235491+0800 HW1[53834:4004545] TopClothes:	Reds	shirt
2021-09-27 17:08:03.235556+0800 HW1[53834:4004545] Trousers:	Greens	jeans
2021-09-27 17:08:03.235616+0800 HW1[53834:4004545] The score is: 0
2021-09-27 17:08:03.235674+0800 HW1[53834:4004545] Day 2
2021-09-27 17:08:03.235730+0800 HW1[53834:4004545] TopClothes:	Blacks	shirt
2021-09-27 17:08:03.235793+0800 HW1[53834:4004545] Trousers:	Browns	jeans
2021-09-27 17:08:03.235850+0800 HW1[53834:4004545] The score is: 19
2021-09-27 17:08:03.236023+0800 HW1[53834:4004545] Day 3
2021-09-27 17:08:03.236460+0800 HW1[53834:4004545] TopClothes:	Blues	shirt
2021-09-27 17:08:03.237164+0800 HW1[53834:4004545] Trousers:	Browns	jeans
2021-09-27 17:08:03.237793+0800 HW1[53834:4004545] The score is: 24
2021-09-27 17:08:03.238044+0800 HW1[53834:4004545] Day 4
2021-09-27 17:08:03.238217+0800 HW1[53834:4004545] TopClothes:	Reds	shirt
2021-09-27 17:08:03.238383+0800 HW1[53834:4004545] Trousers:	Whites	jeans
2021-09-27 17:08:03.238565+0800 HW1[53834:4004545] The score is: 25
2021-09-27 17:08:03.238745+0800 HW1[53834:4004545] Day 5
2021-09-27 17:08:03.238931+0800 HW1[53834:4004545] TopClothes:	Blacks	shirt
2021-09-27 17:08:03.239115+0800 HW1[53834:4004545] Trousers:	Reds	jeans
2021-09-27 17:08:03.239296+0800 HW1[53834:4004545] The score is: 17
2021-09-27 17:08:03.239457+0800 HW1[53834:4004545] Day 6
2021-09-27 17:08:03.239631+0800 HW1[53834:4004545] TopClothes:	Blues	shirt
2021-09-27 17:08:03.239814+0800 HW1[53834:4004545] Trousers:	Greens	jeans
2021-09-27 17:08:03.240010+0800 HW1[53834:4004545] The score is: 23
2021-09-27 17:08:03.242287+0800 HW1[53834:4004545] Day 7
2021-09-27 17:08:03.242371+0800 HW1[53834:4004545] TopClothes:	Blacks	shirt
2021-09-27 17:08:03.242439+0800 HW1[53834:4004545] Trousers:	Whites	jeans
2021-09-27 17:08:03.242501+0800 HW1[53834:4004545] The score is: 15
2021-09-27 17:08:03.242543+0800 HW1[53834:4004545] 
2021-09-27 17:08:03.242601+0800 HW1[53834:4004545] MAX SCORE is: 25
2021-09-27 17:08:03.242686+0800 HW1[53834:4004545] Day 4
2021-09-27 17:08:03.242911+0800 HW1[53834:4004545] TopClothes:	Reds	shirt
2021-09-27 17:08:03.243121+0800 HW1[53834:4004545] Trousers:	Whites	jeans
```

## **四、实验心得**

总的来说本次实验让我对于 OC 编程有了一个初步的认识，接触到了了各种面向对象的特性同 C 语言相结合的奇妙体验，让我对于 OC 的认识更进了一步. 

期待在今后的学习中能够对 OC 编程与 iOS 开发有更加深入的了解. 
