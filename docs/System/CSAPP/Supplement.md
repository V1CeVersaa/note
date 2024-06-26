# Supplement

## Section 1 Foundations of Digital Logic

### 1.2 数字硬件实现

#### 1.2.1 集成电路

**集成电路/Integrated Circuit**是一个硅半导体晶体，包含用来构建逻辑门和存储单元的电子元件，将二极管、晶体管以及其他原件都制作在同一块芯片上，通过陶瓷或者塑料来封装，通过焊接芯片和外界引脚来形成集成电路。

#### CMOS 电路工艺

**CMOS/互补金属氧化物半导体/Complementary Metal-Oxide Semiconductor**工艺具有高密度、高性能与低功耗的优势，是现代数字集成电路的主流工艺。具体观察 CMOS 晶体管的结构，在衬底之上有**栅极/Gate**，栅极之下有**绝缘层/Insulator**，绝缘层之下有**源极/Source**和**漏极/Drain**，源极与漏极之间有一个间隙，一般称之为**沟道**。CMOS 电路中的晶体管有两种类型：**n 沟道晶体管/nMOS**和**p 沟道晶体管/pMOS**。


## Section 2 Combinational Logic Circuit

### 2.x 门的传播延迟

**传播延迟/Propagation delay**是信号的变化从输入传播到输出所需要的时间。电路运行速度与电路中经过门的最长传播延迟成反比关系。

我们有三个传播延迟参数：**高到低的传播时间/High-to-low propagation time**$t_{PHL}$，**低到高的传播时间/Low-to-high propagation time**$t_{PLH}$，**传播延迟/Propagation delay**$t_{pd}$。

在模拟过程对门建模的时候，往往使用传输延迟与惯性延迟。**传输延迟/Transport delay**是指输出响应输入的变化，在指定的传播延迟之后发生改变。**惯性延迟/Inertial delay**类似于传输延迟，但是如果输入变化使输出在一个小于**拒绝时间/Rejection time**的时间内改变，那么两次变化中的第一次将不会发生。拒绝时间是一个确定的值，不大于传播延迟，一般等于传播延迟。

## Section 3 Sequential Logic Circuit

所谓时序逻辑电路，其结果输出不仅仅取决于当前的外界输入，而且取决于系统所处的内部状态，而系统当前的内部状态都是由系统的初态经过前序若干输入信息的处理加工之后到达的状态，所以我们可以认为时序逻辑电路输出的结果不仅仅取决于当前的外部输入，还取决于所有前序输入。但是对于一个简单的电路系统而言，记录所有前序输入是不现实的。通常，我们记录前序输入可能导致的影响结果输出的不同状态，根据这些状态和输入产生的结果输出。

处理时序逻辑的重要理论工具是**有限状态机/Finite State Machine**，有限状态机是一个刻画状态与状态转换的理论工具。在没有任何输入的情况下，系统处于初始状态，随着外部信息的到来，系统状态根据应用逻辑的实际需要，进入相应的下一个状态，系统还可能向外界发出信号，作为对当前输入的响应。

为了解决状态记忆问题，我们设计出了双稳态器件记忆状态信息，这就是下面的锁存器与触发器。

### 3.1 时序电路的定义

### 3.2 锁存器与触发器

#### 3.2.1 SR 锁存器

#### 3.2.2 D 锁存器

#### 3.2.3 边沿触发式触发器

### 3.3 时序电路分析

#### 3.3.1 输入方程

时序电路的逻辑图由触发器与组合逻辑门组成，在组合逻辑电路中，为触发器产生输入信号的组合电路部分可以通过一个布尔函数集合来描述，这个布尔函数集合称为**触发器输入方程/Flip-flop Input Equation**。组合电路的输出端与触发器的输入端项链，输入方程之中使用带有触发器输出符号的下标的触发器输入符号表示依赖变量，比如$D_{A}=AX+BX$就表示本触发器输出为$A$，输入为$AX+BX$。

#### 3.4.2 状态表与状态图

时序电路的输入、输出和触发器状态之间的功能关系可以用一个**状态表/State Table**列出。状态表由四栏组成，分别是**当前状态/Present State**、**输入/Inputs**、**输出/Outputs**和**下一状态/Next State**。当前状态表示触发器在任意给定时刻 t 的状态，输入栏表示在当前状态下的输入，下一状态栏指的是触发器在一个时钟周期之后的状态，可以哦由逻辑图或者触发器的输入方程得到，输出栏表示在当前状态与输入的组合下输出的值。

我们不得不提到时序逻辑电路的分类：根据输出逻辑对其输入信号依赖情况的不同，时序逻辑电路可以分为**Mealy 型电路/Mealy Model Circuit**和**Moore 型电路/Moore Model Circuit**。Mealy 型电路的输出取决于当前状态和输入，而 Moore 型电路的输出仅仅取决于当前状态。


## Section 4 RISC-V