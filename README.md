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