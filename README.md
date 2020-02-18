数字货币探讨
===
&ensp;&ensp;&ensp;&ensp;此处探讨一下数字货币的算法，以期后续有机会实现。数字货币，就是以区块链技术实现的分布式账本。数字货币只是区块链的应用之一，区块链还可以实现电子合约，从而实现更广泛的应用。

### 共识算法 (POW 和 POS)

    &ensp;&ensp;&ensp;&ensp;
    POW是工作量证明算法，即证明我（本矿机）抱着合作的目的，为了产生这个区块已经花了一定的工作量，一般是让矿机凑一个随机数，让整个区块的hash值符合一定条件。
  
  &ensp;&ensp;&ensp;&ensp;
  POS算法,即权益证明算法。POW的缺点是耗费大量电能，而POS算法在POW算法的基础上进行了改进，他主要的思想是限制参与POW游戏的矿机的数量，即符合一定条件的矿机才能用工作量证明来产生新的区块。POS就是要证明自己持有一定的“币龄”（币龄=持有货币数×持币时间），才可有资格挖矿。一旦成功挖出一个区块，则这些“币龄”被消耗掉。

### 区块结构

#### 比特币的区块结构
  &ensp;&ensp;&ensp;&ensp;
  先参考一下比特币的区块结构。

1. 整体结构

数据项|字节长度|字段名|说明
-|-|-|-
Magic NO | 4 | 魔数 | 常数0xD9B4BEF9
Blocksize | 4 | 区块大小 | 用字节表示的该字段之后的区块大小
Blockheader | 80 | 区块头 | 组成区块头的几个字段


#### 区块分类
1. 创世区块

2. 普通区块

3. 检查点区块

4. 分叉区块（软分叉）

#### 交易结构
1. 转账交易

2. 内容交易

3. 链码交易

### 对外接口
1. 受理交易
2. 反馈交易处理情况
3. 获取区块
4. 获取全链
5. 发送/广播区块
6. 获取矿机清单
