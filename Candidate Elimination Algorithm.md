# Candidate Elimination Algorithm


用一个例子说明这个算法（参考自：http://stackoverflow.com/questions/22625765/candidate-elimination-algorithm ）

## 数据集合：

big,   red,  circle,   No  
small, red,  triangle, No  
small, red,  circle,   Yes  
big,   blue, circle,   No  
small, blue, circle    Yes    

## 过程:

1. 开始时 G0 = {[?, ?, ?]}, S0 = {[0, 0, 0]}
2. 遇到第一个例子，是反例，我们需要特化G：
    * G1 = {[small, ?, ?], [?, blue, ?], [?, ?, triangle]}
    * S1 = S0
3. 遇到第二个例子，还是反例，我们继续特化G
    * 对于[small, ?, ?]因为第二个例子中small的出现，需要特化
        * [small, blue, ?], [small, ?, circle]
    * 对于[?, ?, triangle]因为第二个例子中triangle的出现，需要特化
        * [big, ?, triangle], [?, blue, triangle]
    * 消除掉[?, blue, ?]的特化，剩余的是
        * G2 = {[small, ?， circle], [?, blue, ?], [big, ?, triangle]}
        * S2 = S1 = S0
4. 遇到第三个例子，是正例，我们需要一般化S2,并且移除G中不一致的
    * G3 = {[small, ?, circle]}
    * S3 = {[small, red, circle]}

5. 遇到第四个例子，是反例，我们又要特化G
    * 啥也没发生
    * G4 = G3, S4 = S3
6. 遇到最后一个例子是正例，我们要一般化S，移除G中不一致的
    * G5 = {[small, ?, circle]}
    * S5 = {[small, ?, circle]}

## 总结

* S中开始的时候是什么都不行
* G中开始的时候是什么都行
* 遇到正例，我们就删掉G里面不一致的，然后一般化S
* 遇到反例，我们就特化G中被命中的

















