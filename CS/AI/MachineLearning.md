> 学习来源：https://www.coursera.org/specializations/machine-learning-introduction
>
> 老师：吴恩达 Andrew Ng

# 机器学习介绍

## 机器学习应用

1. 语音识别：问 Siri 推荐最近的饭店；
2. 判断垃圾邮件、骚扰电话、诈骗短信等；
3. 搜索提示；
4. 流水线检测瑕疵品；
5. 自动驾驶；
6. 农业、医疗

## 机器学习定义

"Field of study that gives computers the ability to learn without being explicitly programmed. Arthur Samuel (1959)

## 机器学习算法

- Supervised learning: most used
- Unsupervised learning

## 监督学习

监督学习，通过学习，对给定的输入到输出的映射。

- regress: predict values, infinitely many possible outputs
- classification: predict categories, small number of possible outputs

## 无监督学习

无标签的数据。检测异常

- 聚类
- 异常检测：
- 降维：大数据集转化为小数据集

# 监督学习

x: input variable, feature 输入变量 特征

y: ou tput variable, target variable

m: number of training example

(x, y): single training example

$(x^{(i)}, y^{(i)}): i^{th}$ training example

数据集分为：

- 训练集
- 验证集
- 测试集

## 线性回归

- 单变量线性回归：一个输入变量

- 多变量线性回归：多个输入变量

### 单变量线性回归

损失函数：$\frac{1}{2m}\sum_{i=1}^{m} (\hat{y}^{(i)}-y^{(i)})^2 = \frac{1}{2m}\sum_{i=1}^{m}(f_{w,b}(x^{(i)})-y^{(i)})^2 = \frac{1}{2m}\sum_{i=1}^{m}(wx^{(i)}+b-y^{(i)})^2$

使损失函数最小的参数作为模型的参数

单个参数的损失函数是二维图形；2个参数的损失函数图形是3维图形，通常转换为**等高线图**。

学习率 $\alpha$：也称为梯度下降的步长。

$w = w - \alpha \frac{\partial}{\partial w} J(w, b)$

$b = b - \alpha \frac{\partial}{\partial b} J(w, b)$

### 多变量线性回归

引入 x 向量和 w 向量，向量化使得代码简洁，计算速度快。

Numpy 向量化运算，在底层硬件上并行运算。

### 特征缩放

当特征可能取值范围大时，参数选择小的；特征可能取值范围小时，参数选择大的。

特征范围差异大时，会导致梯度下降效率慢。所以进行特征缩放，提高梯度下降效率。

1. 左右范围 除以 最大值
2. 均值归一化：$\frac{x_i-\bar{x}}{x_{max}-x_{min}}$
3. Z 分数归一化：$\frac{x_i-\bar{x}}{\sigma}$

学习曲线趋于平稳时，梯度下降收敛。

### 学习率选择

3 倍增或 10 倍增

### 特征工程

通过直觉，组合或转换原始特征以定义一个新的特征。

### 多项式回归

把 x 幂等级提升

### 正则化的损失函数

$$
\frac{1}{2m}\sum_{i=1}^{m} (\hat{y}^{(i)}-y^{(i)})^2+\frac{\lambda}{2m}\sum_{i=1}^{n}w_j^2
$$

## 逻辑回归

### sigmoid 函数

$$
z = wx + b\\
f(z) = \frac{1}{1 + e^{-z}}
$$

### 决策边界

当 z== 0 时

### 损失函数

$$
J(w, b)=-\frac{1}{m}\sum_{i=1}^{m}[y^{(i)}log(f_{w,b}(x^{(i)})+(1-y^{(i)})log(1-f_{w,b}(x^{(i)}))]
$$

- 过拟合：高方差，过于向训练集妥协，训练集变化时，模型可能变化较大
- 欠拟合：高偏差
- 泛化：模型对不同数据集的支持程度

### 解决过拟合

- 扩大数据集
- 减少特征的使用数量，删去无用特征
- 正则化：缩小参数的大小

###  正则化的损失函数

$$
J(w, b)=-\frac{1}{m}\sum_{i=1}^{m}[y^{(i)}log(f_{w,b}(x^{(i)})+(1-y^{(i)})log(1-f_{w,b}(x^{(i)}))]+\frac{\lambda}{2m}\sum_{i=1}^{n}w_j^2
$$



# 神经网络

输入特征向量 - 经历一个或多个隐藏层 - 输出概率



## 激活函数

- 线性激活函数：负值到正值
- sigmoid 函数：二分类问题
- ReLU函数：非负值 隐藏层默认使用

### Softmax

多分类



