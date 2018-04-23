## 谢飞 330407739 第八周作业 实现Densenet 
Densenet 的代码请见 
- nets/densenet.py

Eval截图请见
- screen_shot_of_eval.png

对growth的理解 
- 如果每一个Dense Connectivity生成k个feature map, name 第l层会生成   - k0 + k *(l-1) 个输入的feature map. 这里的k就是网络的增长率.
- 对于Densenet, 相对比较小的增长率已经可以容纳足够的特征信息.
- 一方面是因为每一层都能获得前面所有feature map 的信息, 所以有一个知识库.
- 特征图则成为了全局的网络状态.每一层增加k个feature map到这个状态里.
- 增长率控制了有多少新的信息被添加到这个全局状态中.
- 全局状态一旦被写入,就可以被网络的任意层访问获得,因此不用像传统网络那样,
- 从一层复制到另一层.


对稠密链接的理解 
- 为了更好的提高信息在层之间的流动,这里提出了一种不同的链接模式.
- 引入了从任意层到所有后续层的全部直接链接.
- 第l层接受前面所有层的feature map, 前面所有层的feature map,
- 是做组合操作,而不是加操作.
