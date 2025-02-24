
- 如果没有要求学生填写日期的格式统一，下次如果想用函数，则必须要求填写格式统一，方便统计；
- 如果下次不想用函数，那也可以要求格式统一，看起来美观。

## 基础操作学习

### 单元格移动

1. 选择单元格的移动，使用 `Tab`，选择目前单元格右边的一个单元格，相当于向右移动；
2. 使用 `Enter`，选择目前单元格下边的一个单元格，相当于向下移动；
3. 使用 `Shift + Tab/Enter`，与上面的操作相反；

### 单元格内容和格式

1. 使用 `F2` 或者 `Shift + F2`,可以直接对单元格目前内容进行修改，而不需要使用鼠标点击才能修改；
2. 选择区域或者某个单元格后，使用 `Ctrl + 1` 可直接进入设置该区域的单元格格式；

## 统一格式操作

	如果学习使用函数进行计算，则需要统一数据格式，如果使用筛选则不需要，但是要对于不同格式的同一日期都要勾选；首先介绍如何使用函数，后面介绍如何筛选。

- 注意：部分学生填写日期的时候自己设置了单元格模式为自定义的日期模式，替换操作不能对这些内容里面的 月和日 字进行替换；目前需要手动修改，*并且这一步需要在替换操作之前进行*；
（确保完成了上一步）
- *替换操作位置*：`开始` 操作栏的最右边的 `放大镜`；
 使用*替换*操作，首先选中离校时间和返校时间两列单元格，将“月”替换为“.”；将“日”替换为“”；（这里就是将 `日` 替换为 `空`,什么内容也不填写）；
![[Pasted image 20240928123534.png|800]]
![[Pasted image 20240928123606.png|800]]

![[Pasted image 20240928123120.png|800]]

## 如何不统一格式进行计数（通配符）

### 通配符的介绍

- 首先介绍三种通配符，依次是 `*`,`?`,`~`；我们通常用他们帮助查找特定内容；
- `*`，可以用来代表任意多个字符；
- `？`，用来代表一个字符；
- `~`，是转义操作符，当你需要 `*` 和 `?` 而不是通配符的 `*` 和 `?` 时候，在他们前面加上 `~`;

这里介绍如何使用通配符来数不同格式的日期，比如： `9.30`,`9月30日`，`9/30`,`9-30`; 但是如果有 `九月三十日`,就不能和前面统一，我们往下看。

这里大致意思就是用 `*` 来代替 9 和 30 之间的字符，以及 30 后面的字符，毕竟我们这里相对统一；这里结果是 15；

![[Pasted image 20240928203850.png|800]]

### 其他使用举例

比如：
- 计算机（一）班，可以使用 `“*（一）*”`，来表示；
- 可以使用 `*15000*`，来表示某一院系的学生。如下表格：

| 学号           | 姓名  | 成绩  |
| ------------ | --- | --- |
| 199915000521 | 临江仙 | 99  |
| 199911000520 | 谒金门 | 66  |
| 199915000666 | 乌夜啼 | 88  |
| 199919000666 | 沁园春 | 100 |
|              |     |     |

### 注意

- 目标区域必须是文本格式，使用前要进行调整，或者在填写表格前就调整到位；
- 使用函数时候，函数的条件部分（也就是函数参数里面的第二部分），要加英文双引号；（在 Excel 的函数面板操作可以不加，但是在单元格内填写必须加）

## 计算人员的操作—使用函数

### 使用 COUNTIF 函数

#### COUNTIF 输入

选中目标单元格，输入 `=COUNTIF` ，在这里可以输入大写或者小写，并且也不用全部输入，输入几个字母就会出现一系列函数，可以选择 COUNTIF；如下图：![[Pasted image 20240928124113.png]]

#### COUNTIF 格式介绍

=COUNTIF(`目标区域`,`判断条件`)，

- 目标区域是我们要数的区域，这里我们每个班级不到 60 人，区域可以填写 `F2:F100`,代表第 F 列的第二行 (最左边是行数，这里不是指序号数）开始，到第一百行，当你填写完毕后会自动框选出来；
- 使用 英文 `，` 隔开；
- 判断条件填写 `9.30`,就是计算选中区域填写的 9.30 的人数；输入回车，计算完毕；计算完毕后如果再次查看这个单元格内的公式，它显示的判断条件是 `9.3`,不必在意。
- ![[Pasted image 20240930164022.png|600]]

## 统计人数介绍

我们以前两天，9.30 和 10.1 的不在校人数为例;

我们都计算当天的不在校人数，在校人数最后用班级人数去减；

### 9.30 不在校人数计算

 `9.30的不在校人数=（9.28+9.29+9.30）的离校人数-（9.28+9.29+9.30）的返校人数`；如果确定这几天没有人返校，或者返校人数很少，那么也可以数一数；但是推荐使用函数公式进行练习；如下图：
   ![[Pasted image 20240928130516.png]]

### 10.1 不在校人数计算

`10.1的不在校人数=9.30不在校+10.1离校-10.1返`，如下图：
![[Pasted image 20240928130713.png]]

### 以此类推

`10.2的不在校人数=10.1不在校+10.2离校-10.2返校`

`10.3的不在校人数=10.2不在校+10.3离校-10.3返校`

`10.4的不在校人数=10.3不在校+10.4离校-10.4返校`

`10.5的不在校人数=10.4不在校+10.5离校-10.5返校`

`10.6的不在校人数=10.5不在校+10.6离校-10.6返校`

`10.7的不在校人数=10.6不在校+10.7离校-10.7返校`

## 计算人员数量—使用筛选

*筛选位置*：数据选项栏 的 左边第三个；

### 操作

1. 首先选中目标列，比如：离校时间一列；然后点击筛选；此时 离校时间的单元格 右上角 出现绿色小三角，点击小三角 进行筛选；如下图：
2. 因为我们第一个统计是 9.30 不在校人数，不管 9.28.9.29，因此就选中 9.28,9.29,9.30；口算记住数据；
3. 然后筛选 9.28，9.29，9.30 返校人数，口算记住数据；二者相减，填入表格中；

`10.1不在校人数=9.30不在校人数+10.1离校人数-10.返校人数` ，与上面相同，再次选中区域进行两次筛选，筛选出来 10.1 离校人数，10.1 返校人数，记住数据。

![[Pasted image 20240928135200.png|800]]
