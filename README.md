# 学业报告单 v2.3

创建在线协作表的目的是汇总各年级各学科的数据，将汇总的数据字段以邮件合并的方式插入到word模板中，最终生成每个学生的学业报告单。

制作在线协作表的过程中，要面向不同的年级和学科。针对老师们提出的个性化需求，创建属于该学科的`sheet` 。

**这里的难点不是编写单元格内的公式，而是充分沟通，切实了解一线老师们的需求，然后再通过技术手段实现相对应的功能。**

<img src="https://cdn.jsdelivr.net/gh/PaulRua/Images/ThinkPadX1/202401161318412.png" alt="202401161318412" style="zoom:33%;" />



# 报告单模板

> **创建word报告单模板是最重要的环节，因为它是面向“第三方”的一个学习过程和成果的“证明”。**

在制作报告单模板的过程中，我也遇到过一些技术问题，下面我将结合自己的经验，把遇到的问题进行汇总整理。



## 页眉页脚

- 页眉页脚中需要注意调整`页眉顶端距离`和`页脚底端距离`，这两个距离太大或太小都容易导致页面布局产生变化。
- 页眉页脚的字体要统一。



## 页面布局

1. Word的页面布局我是通过插入表格来控制的。在一张页面中，首先插入一个大的单元格，有点类似于`HTML`语言中的`div`块，这个单元格用于限定报告单内容的区域。

2. 在创建好的单元格内，插入若干小的单元格，并根据需求进行拆分、合并或插入。

<img src="https://cdn.jsdelivr.net/gh/PaulRua/Images/ThinkPadX1/202401171444200.png" alt="202401171444200" style="zoom:33%;" />

3. 接下来就要对表格属性进行优化。打开表格属性窗口，设置参数如下：

<img src="https://cdn.jsdelivr.net/gh/PaulRua/Images/ThinkPadX1/202401171438045.png" alt="202401171438045" style="zoom: 50%;" />

4. 如果你想要将某个表格和它上方的表格拉开一段距离，可以点击表格属性中的`定位`选项，设置`垂直定位`参数即可，比如`0.2厘米`。

<img src="https://cdn.jsdelivr.net/gh/PaulRua/Images/ThinkPadX1/202401171442973.png" alt="202401171442973" style="zoom: 50%;" />

5. 单元格边距可以个性化调整，比如将每个单元格之间的默认间距设置为`0.04厘米`，这会使表格看起来更整洁（至少在我看来）。

<img src="https://cdn.jsdelivr.net/gh/PaulRua/Images/ThinkPadX1/202401171453955.png" alt="202401171453955" style="zoom:50%;" />

6. 每个单元格的行高可以根据实际需求调整。对于不同的行可以分别设置为`最小值`或`固定值`。
   - `最小值`行高是有**下限**的 :point_down:，行高会根据单元格中的内容进行自适应。
   - `固定值`行高没有**下限** :no_entry_sign::point_down:，只要设置了指定的高度，那这个单元格的行高就不会跟随内容变化而变化。

<img src="https://cdn.jsdelivr.net/gh/PaulRua/Images/ThinkPadX1/202401171456921.png" alt="202401171456921" style="zoom:50%;" />



## 表格样式

1. 表格底纹和边框的颜色均为`# C0504D`
2. 表格的边框设置时需要注意，如果先全选整个表格再设置所有框线，则框线可能会出现对不齐的情况（也许和mac系统有关，我并没有验证）。



## 邮件合并

邮件和并是报告单制作的关键，它可以帮助我们快速批量的生成文档。在我看来，邮件合并的功能就像**生产汽车的自动化流水线——给相同的车刻印不同的车架号。**如果要使用这个功能，那你需要准备两样东西：车（word模板）、车架号列表（excel数据）。

接下来，你需要在车上找一个可以刻印的位置，并把车架号依次刻上去。比如你想批量插入`学生姓名`这个字段，那么具体操作由以下五步构成：

1. 下载对应年级的在线协作表；

2. 在Word模板中，找到`学生姓名`单元格所在的位置；

3. 依次点击`邮件`  `选择收件人`  `使用现有列表`；

4. 选择对应的`sheet`；

5. 点击`插入合并域`，将`学生姓名`这个字段插入到单元格中。

当你插入所有字段后，点击`预览结果`可以很方便的查看每个学生的信息。确认无误后，点击`完成并合并`即可生成一个名为`信函1.docx`的新文档，`信函1`中包含了所有学生的报告单。

至此，Word报告单基本制作完毕。接下来的一章，我将重点介绍雷达图是如何做出来的，请搬好凳子认真观看。



# 制作雷达图

## 创建 `report.xlsx`

报告单中语文、数学、英语、体育学科包含了学生的雷达图，那么如何将雷达图生成并批量插入到word文档里呢？我在这里提供了一种解决方案。

首先，需要制作一个excel，表格内要包含“学生姓名”和具体维度，下面是一个具体样式案例。

| 学生姓名 | 汉语拼音 | 识字写字 | 阅读理解 | 表达交流 | 综合实践 | 计算能力 | 审题能力 | 解决问题 | 实践操作 | 双语能力 | Speaking | Reading | Writing | Use of English | Listening | BMI  | 肺活量 | 50米跑 | 坐位体前屈 | 1分钟跳绳 |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | ------- | ------- | -------------- | --------- | ---- | ------ | ------ | ---------- | --------- |
| 张三     |          |          |          |          |          |          |          |          |          |          |          |         |         |                |           |      |        |        |            |           |
| 李四     |          |          |          |          |          |          |          |          |          |          |          |         |         |                |           |      |        |        |            |           |
| ···      |          |          |          |          |          |          |          |          |          |          |          |         |         |                |           |      |        |        |            |           |

然后，将report.xlsx放到对应的年级目录，下面是各年级目录样式：

1. `\..\报告单项目文件\Y1_RADAR\report.xlsx`
2. `\..\报告单项目文件\Y2_RADAR\report.xlsx`

3. `\..\报告单项目文件\Y3_RADAR\report.xlsx`

4. `\..\报告单项目文件\Y4_RADAR\report.xlsx`

5. `\..\报告单项目文件\Y5_RADAR\report.xlsx`

6. `\..\报告单项目文件\Y6_RADAR\report.xlsx`



## 运行 `radar.py`

### 简介

`radar.py` 调用了`Plotly库`来生成雷达图。在 Plotly 的雷达图（`Scatterpolar`）中，`gridshape` 参数用于定义雷达图网格的形状。这个参数主要有两个可选值：

1. **`'circular'`**: 这个值将网格线绘制为圆形。每个数据点的值沿着从中心点向外的直线放置，而网格线则是完全的圆。
2. **`'linear'`** 或 **`'polygon'`**: 这些值将网格线绘制为多边形（通常是正多边形，如五边形、六边形等）。每个数据点的值仍然沿着从中心点向外的直线放置，但网格线形成了多边形的边。

所以，当你选择 `gridshape='circular'` 时，雷达图的网格线将是圆形的；当你选择 `gridshape='linear'` 或 `gridshape='polygon'` 时，网格线将是多边形的。

这个参数的选择取决于你想要的视觉效果以及数据的呈现方式。圆形网格可能适用于更一般的场景，而多边形网格则可以为图表带来更多的几何感。在具体的应用中，可以根据数据的特性和展示需求选择最合适的网格形状。	

运行该程序时，首先会提示输入要生成的年级序号，如1、2、3，然后程序会自动在指定的年级目录中创建学科目录，并在其内自动生成对应的雷达图。

![202401151707368](https://cdn.jsdelivr.net/gh/PaulRua/Images/ThinkPadX1/202401151707368.png)

### 安装配置

首先确保你有Python3，然后拷贝这个项目到本地。

进入`Academic-Report`项目目录

```
cd .\你存放的项目路径\Academic-Report
```

在你的终端（Windows是cmd）里创建虚拟环境

```python
python -m venv venv
```

激活虚拟环境

```python
.\venv\Scripts\activate  # for windows

source venv/bin/activate # for mac
```

在虚拟环境下安装依赖模块：  

```shell
pip install -r requirements.txt
```

依赖安装好以后，在虚拟环境下执行：  

```python
python radar.py
```



## 运行域代码

现在万事俱备，只欠东风。

你只需要打开制作好的word报告单模板，在需要插入图片的位置输入域命令，结合邮件合并功能即可批量生成雷达图。

下面，我将简单描述下面这段域代码的含义及作用。

```
{ INCLUDEPICTURE "图片路径" \* MERGEFORMAT }

例如 { INCLUDEPICTURE "C:\\..\\报告单项目文件\\Y1_RADAR\\chinese\\张三.png" \* MERGEFORMAT }

含义：“INCLUDEPICTURE” 是插入图片的域代码头部；
		 ”图片路径“ 中需要输入图片具体所在的路径；
		 ”\* MERGEFORMAT“ 用于保持原始格式，可以保留也可以删除这句代码。
		 
作用：这段域代码能够在word指定的位置插入一张来源于计算机本地的图片。
```

### 操作步骤

1. 在word文档中任意位置按下 **`alt+F9`** 切换显示域代码的模式；

2. 在想要插入图片的位置按下 **`control+F9`** 用于插入空白域代码，这时你会看到出现一对花括号{};

3. 在{ }中输入上述域代码，注意雷达图存放的文件路径正确无误，任选一个学生的图片路径即可。

4. 这一步比较关键，是实现对应生成每个学生雷达图的核心步骤。

   - 首先，我们假设已经插入了域代码：

     **`{ INCLUDEPICTURE "C:\\..\\报告单项目文件\\Y1_RADAR\\chinese\\张三.png"  \* MERGEFORMAT }`**

   - 接着，依照邮件合并的步骤，将**`张三`**删除，在该位置插入合并域：**`学生姓名`**。于是，域代码就变成了下面这个样子：

     **`{ INCLUDEPICTURE "C:\\..\\报告单项目文件\\Y1_RADAR\\chinese\\{ MERGEFIELD 学生姓名 }.png"  \* MERGEFORMAT }`**

   - 进行到这一步，是不是就大概明白了？Word 完成邮件合并后会将每个学生所对应的图片插入到对应的位置，但是，这还没有结束！

   - 接着，按下 **`alt+F9`**返回普通模式，然后点击邮件合并菜单中的 **`预览结果`** 选项，紧接着按下 **`control+A`** 全选整篇文档，然后按下 **`F9`** 刷新域代码，这样你应该就能够看到该学生对应的雷达图了。点击雷达图，对其图片格式进行调整，确保图片的高与宽能够适配页面布局。

   - 最后，完成邮件合并，重复上面的步骤：按下 **`control+A`** 全选整篇文档，然后按下 **`F9`** 刷新域代码。恭喜你，现在就能看到每个学生的雷达图了。



# Word拆分

Word拆分的功能我花了很大力气研究，曾尝试用VBA、Python程序实现，也试过使用`Kutools for word插件`。如果你对此感兴趣可以深入了解。不过我最终还是选择使用**WPS超级会员专享功能——文档拆分**功能按照页面数量进行了拆分和整理。



# 文件重命名

文件重命名也是比较重要的，因为拆分后的word文档不是按照学生班级姓名命名的，如果一个一个的去改很麻烦。所以我也编写了一段python脚本自动化完成这件事情。



## 运行 `rename.py`

### 简介

`rename.py`根据 `report.xlsx`中提供的新文件名来重命名指定文件夹中的文件。主要使用了以下方法和原理：

1. **用户输入处理**：通过输入获取指定的年级数字，用于定位特定的文件夹。
2. **文件路径操作**：使用`os`模块来构建文件路径，检查文件夹和文件是否存在。
3. **读取Excel文件**：使用`pandas`库来读取Excel文件，这个文件包含了新的文件名信息。
4. **文件重命名**：遍历Excel文件中的每一行，根据提供的新文件名，使用`os.rename`方法来重命名文件夹中的文件。

### 安装配置 

激活虚拟环境

```python
.\venv\Scripts\activate  # for windows

source venv/bin/activate # for mac
```

在虚拟环境下执行：    

```python
python rename.py
```



# Word to PDF

将 `.docx` 格式批量转换为 `pdf` 格式的方法有很多。在本项目中，我通过调用 `docx2pdf` 第三方模块来实现，具体方法和上面的相同，这里不再赘述。

在虚拟环境下执行：    

```python
python word2pdf.py
```

***PaulRua***
