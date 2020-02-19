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
Transaction counter | 1-9 | 交易计数器 | 该区块包含的交易数量，包含coinbase交易
Transactions | 不定 | 交易 | 记录在区块里的交易信息，使用原生的交易信息格式，并且交易在数据流中的位置必须与Merkle树的叶子节点顺序一致

2. 区块头

字节长度 | 字段 | 说明
-|-|-
4 | 版本 | 区块版本号，表示本区块遵守的验证规则
32 | 父区块头哈希值 | 前一区块的哈希值，使用SHA256(SHA256(父区块头))计算
32 | Merkle根 | 该区块中交易的Merkle树根的哈希值，同样采用SHA256(SHA256())计算
4 | 时间戳 | 该区块产生的近似时间，精确到秒的UNIX时间戳，必须严格大于前11个区块时间的中值，<br>同时全节点也会拒绝那些超出自己2个小时时间戳的区块
4 | 难度目标 | 该区块工作量证明算法的难度目标，已经使用特定算法编码
4 | Nonce | 为了找到满足难度目标所设定的随机数，<br>为了解决32位随机数在算力飞升的情况下不够用的问题，规定时间戳和coinbase交易信息均可更改，以此扩展nonce的位数

3. Coinbase交易信息

&ensp;&ensp;&ensp;&ensp;
一个区块第一个交易规定为coinbase交易，即由挖矿产生的比特币奖励。

字节长度 | 字段 | 说明
-|-|-
4 | 版本 |	这笔交易参照的规则
1-9 | 输入计数器 | 包含的交易输入数量
32 | 交易哈希| 不引用任何一个交易，则值全部为0
4 | 交易输出索引 | 固定为0xFFFFFFFF
1-9 | Coinbase数据长度 | coinbase数据长度
不定 | Coinbase数据 | 在V2版本的区块中，除了需要以区块高度开始外，其它数据可以任意填写。<br>用于extra nonce和挖矿标签。
4 | 顺序号 | 值全部为1，0xFFFFFFFF
1-9|输出计数器|包含的交易输出数量
8|总量|用聪表示的比特币值
1-9|锁定脚本大小|用字节表示的后面的锁定脚本长度
不定|锁定脚本|一个定义了支付输出所需条件的脚本
4|锁定时间|一个区块号或UNIX时间戳

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
