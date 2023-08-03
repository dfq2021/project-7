# project-7
Try to Implement this scheme

# 问题重述
![图片1](https://github.com/jlwdfq/project-7/assets/129512207/ab98f3bf-8eea-422a-a1e0-e12ad49333b7)

根据上图的形式，实现该体系

# 实现方式
1.开始时，我们需要根据线性同余法编写自己的KDF。

2.再实现shuffle()函数：根据一个shuffle种子，然后初始化随机数生成器，再使用random.shuffle()对哈希值列表进行shuffle即可。

关键代码：
```python
seed=random.randint(pow(2,127),pow(2,128))
r=myrandint(pow(2,127),pow(2,128),seed)      
s1=next(r)
s2=next(r)
s3=next(r)
seed_D=next(r)
salt_A=next(r)
salt_B=next(r)
salt_C=next(r)
shuffle_seed=next(r)

```
3.此外还使用了与project-6相同的hash-chain。


关键代码：
```python
pl=[hash_chain4[-1],hash_chain3[0],hash_chain2[1]]
temp=hash_function(pl[0].digest()+pl[1].digest())
a=hash_function(temp.digest()+pl[2].digest())
A=hash_function(str(salt_A).encode('utf-8')+a.digest())

pl=[hash_chain4[-1],str(s2),hash_chain2[-1]]
temp=hash_function(pl[0].digest()+pl[1].encode('utf-8'))
b=hash_function(temp.digest()+pl[2].digest())
B=hash_function(str(salt_B).encode('utf-8')+b.digest())

pl=[hash_chain4[1],hash_chain3[-1],hash_chain2[-1]]
temp=hash_function(pl[0].digest()+pl[1].digest())
c=hash_function(temp.digest()+pl[2].digest())
C=hash_function(str(salt_C).encode('utf-8')+c.digest())

```
# 实验结果
![5316a0efbd6c8f3202ef39f2824473c](https://github.com/jlwdfq/project-7/assets/129512207/30a2df0f-098e-4e9f-8a5e-ac38124fac59)

如图所示，可以直接运行文件中python文件可得到该hashwire的Root： b'\xb8\xb8( s\xad>)\n#\x1b[-\xad\x1cX9u2t\x89Z\xed.\x91\xed\x03J"\x1f\x94\xd6'

运行时间: 1.0006427764892578 ms

# 实验环境
| 语言  | 系统      | 平台   | 处理器                     |
|-------|-----------|--------|----------------------------|
| Cpp   | Windows10 | pycharm| Intel(R) Core(TM)i7-11800H |
# 小组分工
戴方奇 202100460092 单人组完成project7

