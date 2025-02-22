.. _cn_api_fluid_layers_gather_nd:

gather_nd
-------------------------------

.. py:function:: paddle.fluid.layers.gather_nd(input, index, name=None)


该OP是 :code:`gather` 的高维推广，并且支持多轴同时索引。:code:`index` 是一个K维度的张量，它可以认为是从 :code:`input` 中取K-1维张量，每一个元素是一个切片：

.. math::
    output[(i_0, ..., i_{K-2})] = input[index[(i_0, ..., i_{K-2})]]

显然，:code:`index.shape[-1] <= input.rank` 并且输出张量的维度是 :code:`index.shape[:-1] + input.shape[index.shape[-1]:]` 。 

示例：

::

         给定：
             input = [[[ 0,  1,  2,  3],
                       [ 4,  5,  6,  7],
                       [ 8,  9, 10, 11]],
                      [[12, 13, 14, 15],
                       [16, 17, 18, 19],
                       [20, 21, 22, 23]]]
             input.shape = (2, 3, 4)

         - 案例 1:
             index = [[1]]
             
             gather_nd(input, index)  
                      = [input[1, :, :]] 
                      = [[12, 13, 14, 15],
                         [16, 17, 18, 19],
                         [20, 21, 22, 23]]

         - 案例 2:

             index = [[0,2]]
             gather_nd(input, index)
                      = [input[0, 2, :]]
                      = [8, 9, 10, 11]

         - 案例 3:

             index = [[1, 2, 3]]
             gather_nd(input, index)
                      = [input[1, 2, 3]]
                      = [23]


参数
::::::::::::

    - **input** (Tensor) - 输入Tensor，数据类型可以是int32，int64，float32，float64, bool。
    - **index** (Tensor) - 输入的索引Tensor，其数据类型为int32或者int64。它的维度 :code:`index.rank` 必须大于1，并且 :code:`index.shape[-1] <= input.rank` 。
    - **name** (str，可选) - 具体用法请参见 :ref:`api_guide_Name`，一般无需设置，默认值为 None。
    
返回
::::::::::::
shape为index.shape[:-1] + input.shape[index.shape[-1]:]的Tensor|LoDTensor，数据类型与 :code:`input` 一致。


代码示例
::::::::::::

COPY-FROM: paddle.fluid.layers.gather_nd