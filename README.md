# [PlantUML](https://plantuml.com/zh/) 在 [vscode](https://code.visualstudio.com/) 中的使用

## 1. 什么是 UML ？

UML —— 统一建模语言（Unified Modeling Language）是非专利的第三代建模和规约语言。

UML是一种开放的方法，用于说明、可视化、构建和编写一个正在开发的、面向对象的、软件密集系统的制品的开放方法。

UML展现了一系列最佳工程实践，这些最佳实践在对大规模，复杂系统进行建模方面，特别是在软件架构层次已经被验证有效。

### 1.1 UML 的历史

1. 1994 年： UML 可以追溯到 1994 年，[Rational Software](https://www.rationalenterprise.com/) 公司的工程师最早开发出来的语言，后来这个公司开发了 [Rational Rose](https://www.ibm.com/support/pages/ibm-rational-rose-enterprise-7004-ifix001) 这种面向对象的统一建模语言的可视化建模工具。用于可视化建模和公司级水平软件应用的组件构造。
2. 1997 年： UML 被对象管理组织接纳为标准，并在此之后受该组织管理。
3. 2005 年： UML 被国际标准化组织接纳为一种标准，自此，该标准被定期修订以涵盖 UML 的最新版本。

虽然这是一个标准语言，但是大部分情况下，开发者并不会去使用 UML，而是去自己产生非标准的手绘。但是值得庆幸的是，很多非标准的手绘中都有 UML 的元素。

## 2. UML 基本概念

UML 中划分为 模型 和 图形 两大类。

### 2.1 模型

在 UML 系统开发中有三个主要的模型，功能模型、对象模型和动态模型：

```plantuml
@startmindmap
* UML 类型
** 功能模型
*** 从用户的角度展示系统的功能
**** 用例图
** 对象模型
*** 采用 对象、属性、操作、关联等概念展示系统的结构和基础
**** 类别图
**** 对象图
** 动态模型
*** 展示系统的内部行为
**** 时序图
**** 活动图
**** 状态图
@endmindmap
```

### 2.2 图形

UML 2.2 中一共定义了 14 种图示：

1. 结构性图形，强调系统式的建模：
    - 静态图：
        - 类图：描述系统的类集合，类的属性和类之间的关系。
        - 对象图：显示特定时间，建模系统结构的完整或部分视图的图。
        - 包图：描述了构成模型的包之间的依赖关系。
    - 实现图：
        - 组件图：如何互相组织以构建更大的组件或是软件系统的。
        - 部署图：对节点（硬件组件）上工件（软件组件）的物理部署（包括连接方式）进行建模。
    - 剖面图：元模型（metamodel）的层次说明，用来说明内部的构造。
    - 复合结构图：也叫组合结构图，“结构”是指元素之间的相互连接，实例通过通信连接合作以实现某目的。

2. 行为式图形，强调系统模型中触发的事件：
    - 活动图：用于为计算性和组织性过程（即工作流）建模，相关活动之间的数据流也在其覆盖范围之内。
    - 状态图：对象在其生存期间的动态行为，表现为对象所经历的状态序列，引起状态转移的事件，以及因状态转移而伴随的动作。
    - 用例图：用户与系统交互的最简表示形式，展现了用户和与他相关的用例之间的关系。

3. 交互性图形，**属于 行为图形 的子集合**，强调系统模型中的资料流程:
    - 通信图：也叫协作图，根据顺序消息对对象或部分之间的交互进行建模。
    - 交互概述图（UML 2.0）：描述用例的正常流与替代流之间的关系，作为内部协作图。在活动图的基础上，使用“交互框”作为元素，替代活动图中的“活动”。交互框间以“控制流”连接。
    - 时序图（UML 2.0）：描述物件在时间序列中的交叉作用。
    - 时间图（UML 2.0）：一种特定类型的交互图，其重点是时序约束。探索对象在给定时间段内的行为。时序图是序列图的一种特殊形式。时序图和时序图的区别在于轴是颠倒的。

14 中 UML 图表一览：

```plantuml
@startmindmap
*[#Orange] UML 图形
    ** 结构性图形
        ***_ 静态图
            ****[#Skyblue] 类图
            ****[#Skyblue] 对象图
            **** 包图
        ***_ 实现图
            ****[#Skyblue] 组件图
            ****[#Skyblue] 部署图
        *** 剖面图
        *** 复合结构图
    left side
    ** 行为式图形
        ***[#Skyblue] 活动图
        ***[#Skyblue] 状态图
        ***[#Skyblue] 用例图
        *** 交互性图形
    *** 展示系统的内部行为
        **** 通信图
        **** 交互概述图
        ****[#Skyblue] 时序图
        ****[#Skyblue] 时间图
@endmindmap
```

### 2.3 模型和图形的区别

1. UML 图，包括：用例图、协作图、活动图、序列图、部署图、构件图、类图、状态图，是 **模型中信息的图形表达方式，但是 UML 模型独立于 UML 图存在**。

2. UML 的当前版本（UML 2.2）只提供了模型信息的交换，而没有提供图信息的交换。

## 3. PlantUML

### 3.1 支持 9 种 UML 图形

1. PlantUML 支持的 9 种 UML 图形，在上图中已经用天蓝色标注出来了，分别是：

[类图](https://plantuml.com/zh/class-diagram)、[对象图](https://plantuml.com/zh/object-diagram)、[组件图](https://plantuml.com/zh/component-diagram)、[部署图](https://plantuml.com/zh/deployment-diagram)、[活动图](https://plantuml.com/zh/activity-diagram-legacy)、[状态图](https://plantuml.com/zh/state-diagram)、[用例图](https://plantuml.com/zh/use-case-diagram)、[时序图](https://plantuml.com/zh/sequence-diagram)、[时间图](https://plantuml.com/zh/timing-diagram)。

```plantuml
@startwbs
* PlantUML 支持的 UML 图形
** 结构性图形
***[#Skyblue]< 类图
***[#Skyblue]< 对象图
***[#Skyblue] 组件图
***[#Skyblue] 部署图
** 行为性图行
***[#Skyblue]< 活动图
***[#Skyblue]< 状态图
***[#Skyblue]< 用例图
***[#Skyblue] 时序图
***[#Skyblue] 时间图
@endwbs
```

2. PlantUML 中使用 UML 的语法结构：

```UML
@startuml
图形代码段
不同的图例，使用不同的符号或者关键字表示
@enduml
```

3. 其他支持：
    a. 也支持其他常用的图形：
        - [思维导图](https://plantuml.com/zh/mindmap-diagram)
        - [甘特图](https://plantuml.com/zh/gantt-diagram)
        - [WBS —— 工作分解结构](https://plantuml.com/zh/wbs-diagram)
    b. 常用协议配置的支持
        - [Json](https://plantuml.com/zh/json)
        - [YAML](https://plantuml.com/zh/yaml)

### 3.2 支持的文件格式

支持的文件格式有以下几种 ：`*.wsd`、`*.pu`、`*.puml`、`*.plantuml`、`*.iuml`。（`*.wsd` —— 由 WordStar 创建的文档，目前该软件几乎没人使用。）

在 vscode 中，以上 5 中文件格式 UML 图，都可以显示，但是 **在编辑过程中 `*.pu`、`*.puml`、`*.plantuml` 三种格式是支持实时预览的**：

![vscode 实时预览 PlantUML 文件](./assets/03-preview-1.png)

使用文本格式编辑，通过 `Alt + D` 快捷键预览 PlantUML 图表，**需要注意的是，**`Alt + D` 时光标必须在图表代码段内** ：

![vscode 间接预览 PlantUML 文件](./assets/04-preview-2.png)

所以，**建议选取 `*.pu`、`*.puml`、`*.plantuml` 之一作为 PlantUML 文件名后缀。**

### 3.3 在 Markdown 文件中的支持

以安装了 PlantUML 插件和 Markdown 的 vscode 为例，在 Markdown 文件中输入如下 PlantUML 代码段：

```plantumlcode
@startmindmap
* A
** A.1
*** A.1.1
** B
*** B.1
** C
*** C.1
@endmindmap
```

预览效果如下：

```plantuml
@startmindmap
* A
** A.1
*** A.1.1
** B
*** B.1
** C
*** C.1
@endmindmap
```

## 4. UML 的开发软件

### 4.1 UML 开发软件

最为传统的有两个：

1. [IBM Rational Rose Enterprise Edition](https://www.ibm.com/support/pages/ibm-rational-rose-enterprise-7004-ifix001)，这是标准的 UML 开发工具。
2. [Microsoft Visio](https://www.microsoft.com/zh-cn/microsoft-365/visio/flowchart-software)，是一款流程图软件工具和画图软件。

现在已经有很多第三方的（且免费的） UML 建模工具，今天我们主要要聊的就是 [PlantUML](https://plantuml.com/zh/) 这种用代码方式替代拖拖拽拽画 UML 图例的方式。

### 4.2 [vscode](https://code.visualstudio.com/) 中安装 [PlantUML](https://plantuml.com/zh/)

1. 安装 [vscode](https://code.visualstudio.com/)， 假如你还没有的话，可以去 [官网下载](https://code.visualstudio.com/) 下载并安装。
2. 安装 PlantUML:
   2.1 打开网页版 [PlantUML](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)，选择 安装也可以：
   ![PlantUML WEB 安装图示](./assets/02-PlantUML-WEB-Install.png)

   2.2 打开 vscode，打开插件管理（可以通过快捷键 `Ctrl+Shift+X` 打开），搜索 `plantuml` 安装 PlantUML 插件：

   ![PlantUML vscode 安装图示](./assets/02-PlantUML-vscode-Install.png)

   2.3 打开 vscode，`Ctrl+p` 打开全局搜索，输入 `ext install plantuml`，选择 `PlantUML` 下 `安装` 按钮点击即可安装。

### 4.3 vscode 中的快捷键

1. `Alt + D` 预览 PlantUML 当前图表；
2. `Ctrl + P` 打开命令行模式，输入 `>plantuml` 可以查看更多导出功能：

![导出功能](./assets/05-plant-export.png)

## 5. PlantUML 中 UML 图形使用介绍

这里将依次介绍 9 中 UML 图例的 PlantUML 常用语法（详情请见[官方文档](https://plantuml.com/zh/sitemap-language-specification)）。

### 5.1 [类图](https://plantuml.com/zh/class-diagram)

描述系统的类集合，类的属性和类之间的关系。

1. 通用图例一览
```plantumlcode
@startuml
()   圆
<>   菱形
..   表示虚线
--   表示实线
@enduml
```

#### 5.1.1 元素声明

```plantumlcode
@startuml
abstract        抽象
abstract class  抽象(等同abstract)
annotation      注解
circle          圆
()              圆缩写形式
class           类
diamond         菱形
<>              菱形写形式
entity          实例
enum            枚举
interface       接口

Car <|- Bus     扩展
Car *-- Tire    组合
Bus o-- Driver  聚合

在关系之间使用标签来说明时, 使用 : 后接 标签文字。

对元素的说明，你可以在每一边使用 "" 来说明。

在标签的开始或结束位置添加 < 或 > 以表明是哪个对象作用到哪个对象上。
@enduml
```

图-1 类图基本元素

```plantuml
@startuml
note "类图基本元素" as C1

abstract        抽象
abstract class  抽象(等同abstract)
annotation      注解
circle          圆
()              圆缩写形式
class           类
diamond         菱形
<>              菱形写形式
entity          实例
enum            枚举
interface       接口

车  <|- 小汽车
小汽车 "1" *-- "4" 轮子 : 拥有 4 >
小汽车 *-- 发动机 : 驱动 <
小汽车 o-- 千斤顶
小汽车 -- 人 : < 所属
@enduml
```

#### 5.1.2 扩展类用法

```plantumlcode
@startuml
要声明字段和方法，你可以使用符号 : 后面跟着字段或方法的名称。也可以在大括号之间分组 {} 所有字段和方法。

访问权限（方法是实心、变量是空心）：
    - 正方形 私有
    # 菱形   保护
    ~ 三角形 包/类的私有
    + 圆形   公开

可以采用命令 skinparam classAttributeIconSize 0 来展示特殊符号本身。

模板通过类关键字（ "<<" 和 ">>" ）来定义

可以使用 note left of , note right of , note top of , note bottom of 这些关键字来添加备注。
你还可以在类的声明末尾使用 note left, note right,note top, note bottom来 添加备注。
此外，单独用 note 这个关键字也是可以的，使用 .. 符号可以作出一条连接它与其它对象的虚线。

你可以用 < 和 > 来定义类的泛型。
@enduml
```

图-2 类图扩展用法

```plantuml
@startuml
note "类图访问权限控制" as C2

class Object << general >>
Object <|- Array
Object : ~ equals()

note "This is a floating note" as N1

Object .. N1
N1 .. Array

class Array
note left: On last defined class

Array : - Object[] datas
Array : # size()
class Array {
    - int size
    + get_by_index(id)
}
@enduml
```

图-3 显示访问权限文本

```plantuml
@startuml
note "类图访问权限控制显示文本" as C3

skinparam classAttributeIconSize 0

Object <|- Array
Object : ~ equals()
Array : - Object[] datas
Array : # size()
class Array {
    - int size
    + get_by_index(id)
}
@enduml
```

图-4 泛型

```plantuml
@startuml
note "泛型" as C4

class Foo<? extends Element> {
  int size()
}
Foo *- Element
@enduml
```

#### 5.1.3 箭头方向

```plantumlcode
类之间默认采用两个破折号 -- 显示出垂直 方向的线，要得到水平方向的可以像这样使用单破折号 (或者点)。

可以通过改变倒置链接来改变方向

可通过在箭头内部使用关键字， 例如 left, right, up 或者 down，来改变方向

也支持 left to right direction 参数
@enduml
```

图-5 箭头方向

```plantuml
@startuml
note "箭头方向控制" as C5

left to right direction
教室 o- 学生
老师 .o 教室

教室 *-- 椅子
教室 *-up- 黑板
教室 *-- 桌子
@enduml
```

#### 5.1.4 分组继承关系

```plantumlcode
@startuml
可以合并所有的箭头，使用 skinparam groupInheritance, 用阈值(第几组)作为参数。
@enduml
```

图-6 [分组继承关系](http://www.plantuml.com/plantuml/uml/SoWkIImgAStDuIhEpimhI2nAp5L8ByelBV3CoqWjoYn9p4jELJ3aud8qLB2fqTLLS0AnZQ1i8pZJsGWeR0mLDeOpdH5C5sEW2XEe2XCuqnd1T44mNKsu75BpKa3E0W00)

```plantuml
@startuml
note "继承关系分组" as C6

skinparam groupInheritance 3

A1 <|-- B1

A2 <|-- B2
A2 <|-- C2

A3 <|-- B3
A3 <|-- C3
A3 <|-- D3

A4 <|-- B4
A4 <|-- C4
A4 <|-- D4
A4 <|-- E4
@enduml
```

### 5.2 [对象图](https://plantuml.com/zh/object-diagram)

显示特定时间，建模系统结构的完整或部分视图的图。

### 5.3 [组件图](https://plantuml.com/zh/component-diagram)

如何互相组织以构建更大的组件或是软件系统的。

### 5.4 [部署图](https://plantuml.com/zh/deployment-diagram)

对节点（硬件组件）上工件（软件组件）的物理部署（包括连接方式）进行建模。

### 5.5 [活动图](https://plantuml.com/zh/activity-diagram-legacy)

用于为计算性和组织性过程（即工作流）建模，相关活动之间的数据流也在其覆盖范围之内。

### 5.6 [状态图](https://plantuml.com/zh/state-diagram)

对象在其生存期间的动态行为，表现为对象所经历的状态序列，引起状态转移的事件，以及因状态转移而伴随的动作。

### 5.7 [用例图](https://plantuml.com/zh/use-case-diagram)

用户与系统交互的最简表示形式，展现了用户和与他相关的用例之间的关系。

### 5.8 [时序图](https://plantuml.com/zh/sequence-diagram)

描述物件在时间序列中的交叉作用。

### 5.9 [时间图](https://plantuml.com/zh/timing-diagram)

一种特定类型的交互图，其重点是时序约束。探索对象在给定时间段内的行为。时序图是序列图的一种特殊形式。时序图和时序图的区别在于轴是颠倒的。
