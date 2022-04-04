**1、安装**    
pip3 install jieba  

**2、分词**    
1. 精确模式，试图将句子最精确地切开，适合文本分析；
2. 全模式，把句子中所有的可以成词的词语都扫描出来, 速度非常快，但是不能解决歧义；
3. 搜索引擎模式，在精确模式的基础上，对长词再次切分，提高召回率，适合用于搜索引擎分词。  



**3、自定义词典**   
开发者可以指定自己自定义的词典，以便包含 jieba 词库里没有的词。   
用法： jieba.load_userdict(dict_path)   
dict_path：为自定义词典文件的路径   

词典格式如下：   
一个词占一行；每一行分三部分：词语、词频（可省略）、词性（可省略），用空格隔开，顺序不可颠倒。  

示例：  

```python  
# -*- coding: utf-8 -*-
import jieba

# seg_str = "好好学习，天天向上。"

# print("/".join(jieba.lcut(seg_str)))    # 精简模式，返回一个列表类型的结果
# print("/".join(jieba.lcut(seg_str, cut_all=True)))      # 全模式，使用 'cut_all=True' 指定 
# print("/".join(jieba.lcut_for_search(seg_str)))     # 搜索引擎模式


txt = open("测试文本test.txt", "r", encoding='utf-8').read()
###此处userdict为自定义字典
jieba.load_userdict("userdict.txt")
words = jieba.lcut(txt)     # 使用精确模式对文本进行分词
counts = {}     # 通过键值对的形式存储词语及其出现的次数

for word in words:
    if len(word) == 1:    # 单个词语不计算在内
        continue
    else:
        counts[word] = counts.get(word, 0) + 1    # 遍历所有词语，每出现一次其对应的值加 1

items = list(counts.items())
items.sort(key=lambda x: x[1], reverse=True)    # 根据词语出现的次数进行从大到小排序

for i in range(30):
    word, count = items[i]
    print("{0:<5}{1:>5}".format(word, count))
```


