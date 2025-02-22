.. _cn_api_nn_Pad3D:

Pad3D
-------------------------------
.. py:class:: paddle.nn.Pad3D(padding, mode="constant", value=0.0, data_format="NCDHW", name=None)

**Pad3D**

按照 padding、mode 和 value 属性对输入进行填充。

参数
::::::::::::

  - **padding** (Tensor | List[int] | int) - 填充大小。如果是 int，则在所有待填充边界使用相同的填充，
    否则填充的格式为[pad_left, pad_right, pad_top, pad_bottom, pad_front, pad_back]。
  - **mode** (str) - padding 的四种模式，分别为 ``'constant'``, ``'reflect'``, ``'replicate'`` 和 ``'circular'``。
    ``'constant'`` 表示填充常数 ``value``； ``'reflect'`` 表示填充以输入边界值为轴的映射；``'replicate'`` 表示
    填充输入边界值；``'circular'`` 为循环填充输入。默认值为 ``'constant'`` 。
  - **value** (float32) - 以 ``'constant'`` 模式填充区域时填充的值。默认值为 0.0。
  - **data_format** (str)  - 指定输入的 format，可为 ``'NCDHW'`` 或者 ``'NDHWC'``，默认值为 ``'NCDHW'``。
  - **name** (str，可选) - 具体用法请参见 :ref:`api_guide_Name`，一般无需设置，默认值为 None。

返回
::::::::::::
无

代码示例
::::::::::::

COPY-FROM: paddle.nn.Pad3D
