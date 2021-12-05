# 1,backbone,,detectionneck, detectionhead
backbone:  darknet53, resnet,DCN 考虑计算效率问题只在最后一层使用DCN
detectionneck : FPN
detectionhead : v3使用3*3卷积并最后用1*1卷积调整自己所需要的通道数目


# 2,参数初始化
随机初始化: 随机因素较大,一旦选择随机分布选择不当网络优化陷入困境
xavier初始化: 加上方差规范化,保持了输入输出数据分布的一致性, 从而加快收敛
he初始化: 考虑了非线性激活函数(ReLU)的影响,将方差修改为/np.sqrt(node_in/2),能让ReLU网路更快的收敛
xavier and he使用条件:
正向传播时,激活值的方差保持不变,反向传播时,状态值的梯度的方差保持不变
xavier 数据均匀分布,主要针对全连接网络,使用于tanh和softsign
he 正态分布,

# 3,SEnet
结构:残差网络的优化,通过输入W*H*C img,通过一个Global Average Pooling -- FC -- ReLU -- FC -- sigmoid,
第一层的FC会把通道降下来,第二层再把通道升上去,得到和通道数相同的C个权重,每个权重用于给对应的通道加权,

DropBlock

IoU Loss

IoU Loss

IoU Aware

Grid Sensitive

Matrix NMS

CoordConv

SPP
spp polling

L1.L2正则化
