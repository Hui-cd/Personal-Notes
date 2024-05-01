在卷积神经网络中，卷积层输出的特征图（feature map）的大小可以根据输入图像的大小、卷积核的大小、步长（stride）以及边缘填充（padding）的数量计算得出。具体的公式如下：

设：
- 输入图像的大小为 \( n \times n \)
- 卷积核的大小为 \( m \times m \)
- 步长（stride）为 \( s \)
- 填充（padding）的数量（在每边）为 \( p \)

则输出特征图的大小 \( O \) 可以按照以下公式计算：

$$O = \left\lfloor \frac{n + 2p - m}{s} + 1 \right\rfloor \times \left\lfloor \frac{n + 2p - m}{s} + 1 \right\rfloor $$

这里的 $\left\lfloor \cdot \right\rfloor$ 表示向下取整。这个公式给出的是输出特征图的宽度和高度，因为宽和高是相同的（假设输入图像和卷积操作都是正方形的）。
