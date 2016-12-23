# 机器学习复习：ID3算法


1. 描述：

    * 输入：例子集合（正，反）
    * 输出：决策树

2. 信息增益：

    ```python
    # 仅仅是两类的
    # 节点中不同的类越多，那么它的信息量越大，我们选一个属性来降低这个信息量
    def Gain(A):
        return I(p, n) - E(A)
    
    def I(p, n):
        # p 节点正例子数
        # n 节点负例子数
        # 信息 I
        return - p/（p+n） * log(2, p/(p+n)) - n / (p+n) * log(2, n/p+n)
    
   def E(A):
       # pi ni为子节点的正负例子数
       return sum((pi+ni)/(p+n) * I(pi, ni)  for pi, ni in  split(A)
    ```
 
 3. 常见问题
     
     * 不相关属性：以此划分，没什么帮助的属性
     * 不充足属性：属性不够，但是划分还得继续
     * 未知属性：最通常值，决策树（当成类），贝叶斯，等等
 
 4. 属性选择标准：
 
     ```python
     
     def IV(A):
         return -sum(ni/total_n * log(2, ni/total_n) for ni in subnodes)
     
     # using gain(A) / IV(A) 作为属性选择的标准。不仅考虑了信息增益，还考虑了划分的比较简单。
     ```
 
 5. 过拟合：
     
     * 减少错误剪枝：
        
        1. 划分测试集，训练集
        2. 在剪枝不伤害效果时，循环：
           1. 评估剪掉每个可能节点后对在测试集效果的影响
           2. 贪心法剪枝，减掉影响最好的。
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 