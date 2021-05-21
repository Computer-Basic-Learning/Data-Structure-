

## Python项目：读入海明威的小说《老人与海》，使用`jieba`分词，然后使用`WordCloud`模块生成词云。



### 1.下载相关模块

- `jieba`模块
- `wordcloud`模块
- `imread`模块

### 2.读取模块

- ```python
  import re                       #re模块
  import jieba                    #jieba分词模块
  from wordcloud import WordCloud #词云模块
  from imread import*             #读取图片信息模块
  import matplotlib.pyplot as plt #显示图片
  ```

### 3.读取文本

- 创建一个`TXT`文件，将“老人与海”小说导入其中。

- 使用`open`函数读取该`TXT`文件信息。

  ```python
  filename='老人与海.txt'
  with open(filename,encoding='utf-8', errors='ignore') as file_project:
      #属性 encoding（指定要打开文件的编码格式） 和 errors（如遇到错误，忽略，继续执行下面的程序）
      str1=file_project.read()
  ```

### 4.读取词云图片

- ```python
  img=imread('3.jpg')
  ```

### 5.处理文本

1. 文本预处理

   ```python
   pattern = re.compile(u'\t|,|/|。|\n|\.|-|:|;|\)|\(|\?|"') # 定义正则表达式匹配模式
   string_data = re.sub(pattern,'',str1) #将符合模式的字符去除（用空字符替换匹配的字符）
   ```

2. 文本分词

   ```python
   seg_list_exact = jieba.cut_for_search(string_data)  # 搜索模式分词
   													#在精确模式的基础上，对长词再次进行切分
   word=(", ".join(seg_list_exact))
   ```

### 6.生成词云

- ```python
  wc=WordCloud(
      background_color='white',#背景颜色
      mask=img,#背景图片
      max_words=300,#最大词语个数
      max_font_size=50,#最大字体大小
      min_font_size=2,#最小字体大小
      font_path='C:\Windows\Fonts\msyh.ttc',#字体路径
      scale=1.5 #图像密度
  ).generate(word)
  ```

### 7.显示生成词云图片

- ```python
  import matplotlib.pyplot as plt
  
  plt.imshow(wc)#显示wc
  plt.axis('off')#取消坐标轴
  plt.show()
  ```

- 效果图：!<img src="C:\Users\tt\AppData\Roaming\Typora\typora-user-images\image-20201108162236787.png" alt="image-20201108162236787" style="zoom:80%;" />



### 8.保存图片

- ```python
  import matplotlib.pyplot as plt
  
  wc.to_file('4.jpg')
  ```

  

### 完整代码

- ```python
  import re                       #re模块
  import jieba                    #jieba分词模块
  from wordcloud import WordCloud #词云模块
  from imread import*             #读取图片信息模块
  import matplotlib.pyplot as plt
  from random import randint      #生成随机数
  
  #读取一个txt文件
  filename='老人与海.txt'
  with open(filename,encoding='utf-8', errors='ignore') as file_project:
      #小说里有特殊的符号等内容和非法字符
      #故添加属性 encoding 和 errors
      str1=file_project.read()
  
  #读取词云图片
  img=imread('3.jpg')
  
  # 文本预处理
  pattern = re.compile(u'\t|,|/|。|\n|\.|-|:|;|\)|\(|\?|"') # 定义正则表达式匹配模式
  string_data = re.sub(pattern,'',str1)  # 将符合模式的字符去除
  
  # 文本分词
  seg_list_exact = jieba.cut_for_search(string_data)  # 搜索模式分词
  word=(", ".join(seg_list_exact))
  
  #生成词云
  wc=WordCloud(
      background_color='white',#背景颜色
      mask=img,#背景图片
      max_words=300,#最大词语个数
      max_font_size=50,#最大字体大小
      min_font_size=2,#最小字体大小
      font_path='C:\Windows\Fonts\msyh.ttc',#字体路径
      scale=1.5
  ).generate(word)
  
  #显示词云图片
  plt.imshow(wc)
  plt.axis('off')
  plt.show()
  
  #保存词云
  wc.to_file('4.jpg')
  
  ```

  
