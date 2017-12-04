# 基本

NumPy的主要对象是齐次多维数组。它是一个元素表（通常是数字），所有相同的类型，由正整数的元组索引。

![](/assets/import.png)

比如上面的例子，有三个黑框，dimension是3，里面有两个红框，4个蓝框，所以axis=2，length=4.

---

##### ndarray.ndim

阵列的轴数（维度）。在Python世界中，维度的数量被称为_等级_。比如上面的例子中ndim=3，每个黑框中的ndim=2

##### ndarray.shape

数组的尺寸。这是一个整数的元组，指示每个维度中数组的大小。对于有n行m列的矩阵，形状将是（n，m）。形状元组的长度 因此是等级或维数 ndim。

##### ndarray.size

数组元素的总数。这等于形状的元素的乘积。相当于“体积”。

##### ndarray.dtype

一个描述数组中元素类型的对象。可以使用标准的Python类型创建或指定dtype。另外NumPy提供它自己的类型。numpy.int32，numpy.int16和numpy.float64是一些例子。

##### ndarray.itemsize

数组中每个元素的字节大小。例如，类型为float64的元素的数组具有项目大小 8（= 64/8），而类型complex32中的一个具有项目大小 4（= 32/8）。这相当于ndarray.dtype.itemsize。

##### ndarray.data

包含数组的实际元素的缓冲区。通常，我们不需要使用这个属性，因为我们将使用索引设施访问数组中的元素。



