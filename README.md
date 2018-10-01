# <font size=4>Day 1 - Data Preprocessing</font>

> <font color=red>**Step 1：导入需要的库**</font>

&emsp;`Numpy`和`Pandas`库几乎是每次都要导入的重要的库。`Numpy`库**包含了一些数学函数以及矩阵等功能**，`Pandas`库**用于导入和管理数据集**

> <font color=red>**Step 2：导入需要的数据集**</font>

&emsp;数据集通常是以`.csv`的格式获取，`CSV`文件是**在纯文本文件中存储的列表数据**。文件的每一行都是一条数据记录，我们使用`Pandas`中的方法`read_csv`来读取本次的CSV文件，读取的数据就是`DataFrame`形式。然后我们**从`DataFrame`中分离出自变量和因变量的矩阵和向量形式**。

> <font color=red>**Step 3：处理缺失值**</font>

&emsp;我们得到的数据很少是完整的，数据可能因为各种原因丢失，需要进一步处理以免影响机器学习模型的表现。我们==可以使用每一列的`Mean`或者`Median`来替换**缺失值**==，通常<font color=red>**使用`sklearn.preprocessing`中的`Imputer`类**</font>来实现。

> <font color=red>**Step 4：编码分类数据**</font>

&emsp;**分类数据**是*包含标签值而不是数据的变量*，可能值的数量一般限于一个固定的集合中。比如`Yes`和`No`这样的值是无法在模型的数学等式中使用的，所以我们**需要将这样的变量编码为数字类型**。这里我们可以使用<font color=red>**`sklearn.preprocessing`中的`LabelEncoder`**</font>来实现。

> <font color=red>**Step 5：将数据集划分为测试集和训练集**</font>

&emsp;我们要将数据集分为两个部分，**用于训练模型的那部分称为`training set`，用于测试训练好的模型表现的称为`test set`**，划分的比例一般是==80/20==。可以导入<font color=red> **`sklearn.crossvalidation`中的`train_test_split()`方法** </font>来实现。

> <font color=red>**Step 6：特征缩放**</font>

&emsp;大部分机器学习算法都会在**两个数据点之间距离计算**中使用==欧几里得距离==，而不同特征在**幅值、单位以及范围**上明显不同就会引发一些问题。在计算距离时，*高幅值的特征所占的权重明显高于低幅值的特征*。解决这个问题的方式就是使用**特征标准化**或者**Z-score归一化**，可以导入<font color=red>**`sklearn.preprocessing`中的`StandardScalar`**</font>来处理。



---

# <font size=4>Day 2 - Simple Linear Regresssion</font>

## <font size=3 color=blue>**使用单个特征预测结果**</font>

&emsp;这是一种基于 **自变量(X)** 的值来预测 **因变量(Y)** 的方法，这种方法假设两个变量是==线性相关的==。所以，我们尝试找一个*线性函数*尽可能准确地预测**响应值(y)**，来作为特征或者说自变量(x)的函数。

## <font size=3 color=blue>**如何找到最佳拟合线**</font>

&emsp;在这个回归模型中，我们尝试通过找到*最佳拟合线* 来**最小化预测误差**，也就是说回归线所造成的误差是最小值。我们要做的是最小化 **观测值$Y_i$** 和 **预测值$Y_p$** 之间的长度。
<br/></br>

> <font color=red>**Step 1：数据预处理**</font>

&emsp;采用和之前一样的进行数据预处理的流程图：
- 导入库
- 导入数据集
- 检查缺失值
- 划分数据集
- 使用简单线性回归模型中用到的库进行特征缩放

> <font color=red>**Step 2：使用训练集训练简单线性模型**</font>

&emsp;这里使用来自<font color=red>**`sklearn.linear_model`**</font>库的<font color=red>**`LinearRegression`**</font>来将数据集训练成模型。然后我们**创建一个`LinearRegression`类的<font color=red>`regressor`</font>对象**，最后在使用`LinearRegression`类中的`fit()`方法基于数据集训练这个`regressor`对象。

> <font color=red>**Step 3：预测结果**</font>

&emsp;现在我们可以根据测试集数据来预测观测值，使用 **向量`Y_pred`** 来存储输出。接着再基于在上一步训练的`regressor`对象，**使用`LinearRegression`的<font color=red>`predict`</font>方法**来预测结果。

> <font color=red>**Step 4：可视化**</font>

&emsp;最后一步是可视化结果，这里使用`matplotlib.pyplot`库来创建训练集结果和测试集结果的散点图，观察和我们模型的预测值的距离。