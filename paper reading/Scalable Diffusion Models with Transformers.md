U-net
pixelcnn++
 vit
 diffusion models are trained to learn the reverse process that inverts forward process corruptions 
Diffusion Model 的合成过程是通过一次次迭代在噪声中提取出所需要的图像/音频 随着迭代步数的增加，合成质量也在越来越好

Gaussian diffusion models

pachify : DiT 的input 的空间表示z （for 256 × 256 × 3 images, z has shape 32 × 32 × 4)）将 spatial input into a sequence of T tokens, each of dimension d. 

在pachify之后，使用基于vit频率的positional embedding, to all input tokens 

input token -> transformer block 

4 种transformer block 去处理条件输入（附加条件信息，例如噪声时间步长 t、类标签 c、自然语言）

In-context conditioning
 append t and c embedding vector in input sequence
Cross-attention block
在multi-head self-attention 之后加了一个 multi-head cross attention ，将t and c embedding 到length-two sequence，通过cross attention 处理 t 和c


### SiLU函数的特点

- **非线性**：SiLU是一个非线性函数，这使得它在深度神经网络中非常有用，因为非线性激活函数可以帮助网络学习复杂的数据表示。
- **平滑性**：与ReLU相比，SiLU是一个平滑的函数，这意味着它的导数（梯度）在整个输入空间内都是定义良好的。这有助于改善网络的优化过程，因为梯度更新更加稳定。
- **自适应门控**：SiLU通过其Sigmoid部分可以看作是一种自适应的门控机制，能够根据输入自动调整激活程度。这使得网络能够更加灵活地学习数据中的特征。