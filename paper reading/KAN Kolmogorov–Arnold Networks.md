MLP place fixed activation functions on nodes
KANs place learnable activation functions on edges
KANs have no linear weight matrices at all, each weight parameter is replaced by a learnable 1D function parametrized as a spline
KANs nodes simply sum incoming signals without applying any non-linearities.

a 2-Layer width-10 KAN is 100 times more accurate than a 4-Layer width-100 MLP (10−7 vs 10−5 MSE) and 100 times more parameter efficient (102 vs 104 parameters).

KANs ususally allow much smaller computation graphs than MLPs

KANs are nothing more than combinations of splines and MLPs 

Splines are accurate for low-dimensional functions, easy to adjust locally and able to switch between different resolutions

splines have a serious curse of dimensionality (COD) problem 

if f is a multivariate continuous function on a bounded domain, then f can be written as a finite composition of continuous functions of a single variable and the binary operation of addition

在多变量函数的表达上，加法是唯一真正的多变量函数