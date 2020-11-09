# Digital_IC_Backend_Interview 数字后端面试题精选（附参考答案）
A collection of possible interview questions for ASIC PD position
---
1.setup和hold time、transition time的概念； 
  
  
2.跨时钟域信号传输的方法；  

3.STA中Constraints有哪些内容，是怎么实现的；  
  

4.为什么要设置case analysis？
5.简单介绍下clock gating的概念。
6.设计过程中，如何处理跨时钟域的问题。
7.简单介绍下ASIC设计从前端到后端的流程，以及每个阶段用到的EDA工具。
8.简单介绍下你对逻辑综合的理解。
9.STA中，clock skew的概念，如何消除skew？
（1）通过在时钟树上使用lvt cell、中驱动cell或者插inverter增加驱动等方式使得clk路径延时降低，可以减小delay的variations，进而降低clock间的skew；
（2）使用高层金属对时钟布线；
（3）减少时钟树的non-common part；
（3）采用inv，而不是buffer，因为缩短时钟树长度有利于减少skew。
10.综合过程中的clock是怎么定义的？
11.如果综合中timing比较差，有哪些优化的方法？
12.实际的综合或STA中，skew如何影响setup和hold检查？有setup/hold violation的话如何调skew？
13.为什么要用clock uncertainty？skew和uncertainty有关系吗？
clock skew和clock uncertainty基本上没有任何关系。uncertainty是指jitter、ocv等无法直接计算的情况，需要在设置uncertainty时人为指定，而skew在CTS之后是可以通过计算得到的，因此不算是uncertainty。综合中在set_clock_uncertainty时考虑skew只是为了模拟/预估这一部分skew，避免pre-CTS过于乐观。
【总结】clock uncertainty在PD不同阶段的设置
（1）pre-CTS：由于没有clock tree skew，clock uncertainty = PLL jitter + skew + margin
（2）post-CTS：clock skew通过clock tree确定，clock uncertainty中没有skew
14.什么是OCV？什么要在综合或者STA过程中做OCV？业界中有哪些种类的OCV？
