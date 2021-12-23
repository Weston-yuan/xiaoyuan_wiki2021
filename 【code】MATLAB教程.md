### 一、介绍  

* MATLAB是m语言的IDE编译器  
* 文件格式 .m    
* 推荐采用实时脚本编写脚本，用命令行debug   

**基本语法（命令）：**   

```
%注释  
%变量名区分大小写，推荐驼峰命名法   
%look for 找函数   
%help 函数名  
%whos   
```  

数据类型    

```
%matlab是弱语言，不需强制定义数据类型，编译器每次执行前推导   
1、数值阵列（类型）：  
整形(int8/uint8/int16/uint16)      
浮点型（single / double）    
2、字符阵列：字符、字符串  
3、胞体/元祖阵列（重点）   
4、结构体阵列   
5、逻辑阵列（布尔类型）   
6、函数句柄阵列  

*其他：Inf 正无穷、-Inf 负无穷、NaN 非数值量
```

函数  
输入函数：disp / input   
取整函数：floor / ceil / round / fix

ga算法：实时脚本——任务task——优化optimize——GA


### 四、MATLAB深度学习tool   

参考教程：   
mat官[方WordByWord生成](https://ww2.mathworks.cn/help/deeplearning/ug/word-by-word-text-generation-using-deep-learning.html?lang=en)    
[YouTube教程](https://www.youtube.com/watch?v=SFwCWN_u-kI)   

这里训练能否启动与数据集有关，官方示例文本data竟然跑不通！   
 ```matlab
 % 加载训练数据html
% url = "http://jhsjk.people.cn/article/32296476";
%%% 竟然和数据源有关系？？？官方的文本数据示例链接竟然跑不通？？？？
url = "https://www.gutenberg.org/files/1184/1184-h/1184-h.htm";
code = webread(url);

% 解析 HTML 代码
% 使用 htmlTree 解析 HTML 代码，然后找到元素名为 "p" 的所有元素，来提取相关文本。
tree = htmlTree(code);
selector = "p";
subtrees = findElement(tree,selector);

% 使用 extractHTMLText 从 HTML 子树中提取文本数据，并查看前 10 段。
textData = extractHTMLText(subtrees);
textData(1:10)

% 删除空段落并查看更新后的前 10 个段落。
textData(textData == "") = [];
textData(1:10)

%用文字云可视化文本数据
figure
wordcloud(textData);
title("Alice's Adventures in Wonderland")

%%%准备要训练的数据
% 使用 tokenizedDocument 对文本数据进行分词。
documents = tokenizedDocument(textData);

% 自定义小批量数据存储——使用分词后的文档创建文档生成数据存储。
%% 此步要将 documentGenerationDatastore.m 保存到路径。
ds = documentGenerationDatastore(documents);
% 按序列长度对数据存储中的文档进行排序。
ds = sort(ds);

%%% 创建和训练 LSTM 网络
inputSize = 1;
embeddingDimension = 100;
numWords = numel(ds.Encoding.Vocabulary);
numClasses = numWords + 1;

% layers为网络的架构，也就是指网络每层的处理模式。
layers = [ 
    sequenceInputLayer(inputSize) %输入层
    wordEmbeddingLayer(embeddingDimension,numWords)
    lstmLayer(100)
    dropoutLayer(0.2)
    fullyConnectedLayer(numClasses) %全连接层
    softmaxLayer
    classificationLayer]; %分类层

%options为超参数的设置，包括学习率，优化方法，迭代次数以及批量大小问题等。
%% 指定训练选项。指定求解器为 'adam'。进行 300 轮训练，学习率为 0.01。将小批量大小设置为 32。要保持数据按序列长度排序，请将 'Shuffle' 选项设置为 'never'。要监控训练进度，请将 'Plots' 选项设置为 'training-progress'。要隐藏详细输出，请将 'Verbose' 设置为 false。
options = trainingOptions('adam', ...
    'MaxEpochs',300, ...
    'InitialLearnRate',0.01, ...
    'MiniBatchSize',32, ...
    'Shuffle','never', ...
    'Plots','training-progress', ...
    'Verbose',false);

% 使用 trainNetwork 训练网络。
%% 这里数据集较小的话，不够神经网络的深度，会报错！！！
% 这里ds为小批量数据，在这里卡了很久了，报错：无效的训练数据！！！
net = trainNetwork(ds,layers,options);
%%% 以上训练过程对Mac来说太漫长，需较高规格的硬件GPU训练
 ```
 
 
 


