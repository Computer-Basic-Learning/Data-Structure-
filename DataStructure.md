# 第一章

---

## 1 绪论

### 1.1 数据结构的定义：

- 在任何问题中，数据元素都不是孤立存在的，而是在它们之间存在着某种关系，这种数据元素相互之间的关系称为结构（Structure）。数据结构是相互之间存在一种或多种特定关系的数据元素的集合。数据结构包括三方面的内容：逻辑结构、存储结构和数据的运算。数据的逻辑结构和存储结构是密不可分的两个方面，一个算法的设计取决于所选定的逻辑结构，而算法的实现依赖于所采用的存储结构。

### 1.2 数据的定义：

### 1.3 数据元素，数据项：

### 1.4 数据的逻辑结构：

- 逻辑结构分类
  - 集合
  - 线性结构
  - 树形结构
  - 图状结构(网状结构)

### 1.5 数据的物理结构（存储结构）

- 物理结构分类
  - 顺序存储
  - 非顺序存储
    - 链式存储
    - 索引存储
    - 散列存储
- 注：数据存储结构的影响
  - 影响存储空间分配的方便程度
  - 影响对数据运算的速度

### 1.6 数据运算：

### 1.7 数据类型：

### 1.8 抽象数据类型：

---

## 2 算法的基本概念

### 2.1 什么是算法

### 2.2 算法的特性

1. 有穷性：有限步之后结束
2. 确定性：不存在二义性，即没有歧义
3. 可行性：比如受限于计算机的计算能力，有些算法虽然理论上可行，但实际上无法完成。
4. 输入：能被计算机处理的各种类型数据，如数字，音频，图像等等。
5. 输出：一至多个程序输出结果。

### 2.3 优质算法所具有的特质

- 确定性
- 可读性
- 健壮性
- 高效性与低存储量需求
  - 执行速度快，时间复杂度低
  - 不费内存，空间复杂度低

---

## 3 算法的时间复杂度

- *时间开销与问题规模n之间的关系*

### 3.1 决定算法时间开销的因素

- 和机器性能有关
- 和编程语言有关
- 和编程程序产生的机器指令质量有关
- 有些算法不能事后统计时间复杂度

### 3.2 算法的时间复杂度定义

- 事先预计算法时间开销*T(n)* 与问题规模*n* 的关系

- 大O表示“同阶”，同等数量级。即当n->正无穷时，二者之比为常数

- 例：$T=3n   =>   T(n)=O(n)$

- 计算规则：
  
  - 加法规则：$T(n)=T_1(n)+T_2(n)=O(f(n)+O(g(n)))=O(max(f(n)+g(n)))$ 
    
    **多项相加，只保留阶数最高的项，且系数变为1**
  
  - 乘法规则：
    
    $T(n)=T_1(n)*T_2(n)=O(f(n))*O(g(n))=O(f(n)*g(n))$
    
    **多项相乘，都保留**
  
  - 注：$O(1)<O(log_2n)<O(n)<O(nlog_2n)<O(n^2)<O(n^3)<O(2^n)<O(n!)<O(n^n)$

### 3.3 时间复杂度分类

- 最坏时间复杂度

- 平均时间复杂度

- 最好时间复杂度（不重要）

---

## 4 算法的空间复杂度(S=S(n))

### 4.1 空间复杂度的分类

- 算法原地工作---算法所需的空间为常量

- 其他

### 4.2 内存开销

- 存储变量

- 函数调用（例：递归调用，空间复杂度=递归调用的深度(**一般情况下**)）

---

# 第二章：线性表

---

## 1 线性表的定义与基本操作

### 1.1 线性表的定义

- 线性表是具有相同数据类型（*所占空间一样大*） 的 *n(n>=0)* 个数据元素的有限序列，其中n为表长，当 *n=0* 时线性表是一个空表。
  
  $L=(a_1,a_2,a_3,.....,a_n)$

- 几个需要注意的点
  
  - $a_i$是线性表中的“第i个”元素在线性表的位序
  
  - $a_1$是表头元素，$a_n$是表尾元素
  
  - 除第一个元素外，每个元素有且仅有一个**直接前驱**，除最后一个元素外，每个元素有且仅有一个**直接后继**

### 1.2 线性表的基本操作

1. `InitList(&L): `:初始化链表

2. `DestoryList(&L)`:销毁链表

3. `ListInsert(&L,i,e)`:插入操作

4. `LocateDelete(&L,i&e)`:删除操作

5. `LocateElem(L,e)`:安值查找操作

6. `GetElem(L,i)`:按位查找操作

7. `Length(L)`:求表长

8. `PrintList(L):`输出操作

9. `Empty(L)`判空操作
- **传入参数的引用“&”------对参数的原本进行引用（C++）**

---

## 2  顺序表的定义

### 2.1  顺序表的定义

- 用顺序存储的方式实现线性表顺序存储。把逻辑上也相邻的存储单元中，元素之间的关系由存储单元的邻接关系来体现。

### 2.2 顺序表的实现

1. 静态分配：(长度不可改变)
   
   ```cpp
   //静态分配
   #define Maxsize 10
   typedef struct {
       Elemtype data[Maxsize];
       int length;  
   }SqList;
   //初始化顺序表(静态分配)
   void InitList(SqList& L){
       for (int i = 0; i < MaxSize; i++)
           L.data[i] = 0;
       L.length = 0;
   }
   ```

2. 动态分配：
   
   ```cpp
   #define InitSize 10
   typedef struct{
       Elemtype *data;
       int Maxsize;
       int length;
   }SeqList;
   //声明一个顺序表(动态分配)
   void InitList(SeqList& L) {
       L.data = (int*)malloc(sizeof(int) * InitSize);
       L.length = 0;
       L.MaxSize = InitSize;
   }
   ```
- 动态申请，释放内存空间（malloc，free函数）
  
  例：`L.data=(ElemType*)malloc(sizeof(ElemType)*InitSize);`

### 2.3 顺序表的特点

- 随机访问，即可在O(1)时间内找到第i个元素。

- 存储密度高，每个结点只存数据元素。

- 拓展容量不方便

- 插入，删除不方便

---

## 3 顺序表插入，删除操作

### 3.1 插入操作

- `ListInsert(&L,i,e)`:在表L第i个位置上插入指定位置元素e
  
  ```cpp
  //在i位置插入e
  bool ListInsert(SqList& L, int i, int e) {
      if (i<1 || i>L.length + 1)
          return false;
      if (L.length >= MaxSize)
          return false;
      for (int j = L.length; j >= i; j--)
          L.data[j + 1] = L.data[j];
      L.data[i - 1] = e;
      L.length++;
      return true;
  }
  ```

### 3.2 插入操作的时间复杂度分析

- 分析最深层循环语句的执行次数与问题规模*n*的关系。

- 三种情况：
  
  - 最好时间复杂度：插入表尾，T=O(1)
  
  - 平均时间复杂度：插入每个位置的概率相同：
    
    平均循环次数=np+(n-1)*p+......+1p=....=n/2
    
    **====>T=O(n)(平均时间复杂度)**
  
  - 最坏时间复杂度：插入表头，T=O(n)

### 3.3 删除操作

- `ListDelete(&L,i,&e)`:删除表中第i个位置的元素，并用e返回删除元素的值。
  
  ```cpp
  //删除i位置的e
  bool ListDelete(SqList& L, int i, int& e) {
      if (i<1 || i>L.length + 1)
          return false;
      e = L.data[i - 1];
      for (int j = i; j < L.length; j++)
          L.data[j - 1] = L.data[j];
      L.length--;
      return true;
  }
  ```

### 3.4 删除操作时间复杂度（与插入操作情况相同）

- 时间复杂度三种情况
  
  - 最好：T=O(1)
  
  - 平均：T=O(n)
  
  - 最坏：T=O(n)**<==>(n-1)*p+....+1P**

____

## 4 顺序表的查找操作

### 4.1 按位查找操作

- `GetElem(L,i)`:获取第i个位置的元素的值。
  
  - 静态分配：
    
    ```cpp
    //静态分配按位查找
    ElemType GetElem(SeqList L,int i){
        return L.data[i-1];
    }
    ```
  
  - 动态分配：
    
    ```cpp
    //动态分配按位查找
    ```

- 时间复杂度：O(1)

### 4.2 按值查找操作

- `LocateElem(L,e)`:在表L中找给定关键字值的元素。
  
  ```cpp
  //按值查找操作
  int LocateElem(SeqList L,int e){
      for(int i=0;i<L.length;i++)
          if(L.data[i]==e)
              return i++;
      return 0;
  }
  ```

- 时间复杂度：
  
  - 最好：T=O(1)
  
  - 最坏：T=O(n)
  
  - 平均：T=O(n)

- 注：**判断两个结构相等不可以直接用‘==’**

---

## 5 单链表的定义

### 5.1 关于单链表

- 什么是单链表
  
  - 

- 单链表的有缺点
  
  - 优点：不要求大片连续空间，改变容量方便。
  
  - 缺点：不可随机存取，要耗费一定空间存放指针。

- **单链表的局限性：无法逆向检索**

### 5.2 用代码定义一个单链表

- ```cpp
  //定义一个单链表
  typedef struct LNode {
      int data;
      struct LNode* next;  //指针指向下一个节点
  }LNode, * LinkList;
  ```

- 注：
  
  - **使用LinkList强调这是一个单链表。**
  
  - **使用LNode*强调这是一个结点。**

### 5.3 初始化一个单链表

1. 定义不带头结点的单链表
   
   ```cpp
   //不带头结点的单链表
   bool InitList_NoHead(LinkList& L) {
       L = NULL;
       return true;
   }
   ```

2. 定义带头结点的单链表(写代码更方便)
   
   ```cpp
   //带头节点的单链表
   bool InitList_WithHead(LinkList& L) {
       L = (LNode*)malloc(sizeof(LNode));
       if (L == NULL)
           return false;   //内存不足，分配失败
       L->next = NULL;     //头结点为空，之后暂时无节点
       return true;
   }
   ```

3. 判空
   
   ```cpp
   //判断一个链表是否为空
   bool Empty(LinkList& L) {
       return (L->next == NULL);
   }
   ```

--- 

## 6 单链表的插入和删除

### 6.1 后插操作

- `InsertNextNode(LNode* p,int e)`:在指定结点p后插入元素e。

- 代码示例：
  
  ```cpp
  //后插操作：在p结点之后插入元素e
  bool InsertNextNode(LNode* p, int e) {
      /*此操作可代替在指定位置插入元素的插入操作*/
      if (p == NULL)
          return false;
      LNode* NextNode = (LNode*)malloc(sizeof(LNode));
      if (NextNode == NULL) //内存分配失败
          return false;
      NextNode->data = e;     //在NextNode中保存数据元素e；
      NextNode->next = p->next;
      p->next = NextNode;
      return true;          //将结点NextNode连接到p之后；
  }
  ```

### 6.2 前插操作

- `InsertPriorNode(LNode* p,int e)`:在指定结点p前插入元素e。

- 代码示例：
  
  ```cpp
  //前插操作：在p结点之前插入元素e
  bool InsertPriorNode(LNode* p, int e) {
      if (p == NULL)
          return false;
      LNode* PriorNode = (LNode*)malloc(sizeof(LNode));
      if (PriorNode == NULL)
          return false;  //内存分配失败
      PriorNode->next = p->next;
      p->next = PriorNode;
      PriorNode->data = p->data;
      p->data = e;
      return true;
  }
  ```

### 6.3 插入操作

- `ListInsert_WithHead(&L,i,e)`:在表中的第i个位置上插入指定元素e(带头结点)。
  
  - 平均时间复杂度：T=O(n)
  
  ```cpp
  bool LinkList_WithHead(LinkList& L, int i, int e) {
      if (i < 1)
          return false;
      LNode* p;     //指针p指向当前扫描到的节点
      int SubToNode = 0; //当前p指向的是第几个节点
      p = L;
      while (p != NULL && SubToNode < i - 1) {
          //循环找到第i-1个节点
          p = p->next;
          SubToNode++;
      }
      InsertNextNode(p,e);
  }
  ```

- `ListInsert_NoHead(&L,i,e)`：在表中的第i个位置上插入指定元素e(不带头结点)。
  
  - 平均时间复杂度：T=O(n)
  
  - 注：**相比带头结点，不带头结点的链表的代码更加复杂，需要分情况讨论。**
  
  ```cpp
  bool ListInsert_NoHead(LinkList& L, int i, int e) {
      if (i < 1)
          return false;
      if (i == 1) {
          LNode* InsertLNode = (LNode*)malloc(sizeof(LNode));
          InsertLNode->data = e;
          InsertLNode->next = L;
          L = InsertLNode;
          return true;
      }
      LNode* p;  //指针p当前扫描到的结点
      int SubToLNode = 1;   //当前p指向第几个结点
      p = L;
      while (p != NULL && SubToLNode < i - 1) {
          p = p->next;
          SubToLNode++;
      }
      InsertNextNode(p,e);
  }
  ```

### 6.4 删除指定结点

- `DeleteNode(LNode* p,&e)`:删除操作-----删除表L中第i个位置的元素，并用e返回被删除元素的值。
  
  ```cpp
  //删除指定结点p
  bool DeleteNode(LNode* p) {
      if (p == NULL)
          return false; //i值不合法
      LNode* DeleteNode = p->next;    //令DeleteNode指向*p的后继结点
      p->data = p->next->data;           //和后继结点交换数据域
      p->next = DeleteNode->next;     //将DeleteNode从链中断开
      free(DeleteNode);               //释放DeleteNode的存储空间
      return true;
  }
  ```

### 6.5 按位序删除(带头结点)

- `ListDelete(&L,i,&e)`:按位删除-----删除表L中第i个位置的元素，并用e返回被删除元素的值。
  
  ```cpp
  //按位序删除操作：（带头结点）
  //若指导链表头指针，可遍历到要删除的，然后删除
  bool ListDelete(LinkList& L, int i, int& e) {
      if (i < 1)
          return false;
      LNode* p;
      int SubPointNode = 0;
      p = L;
      while (p != NULL && SubPointNode < i - 1) {
          p = p->next;
          SubPointNode++;
      }
      if (p == NULL)
          return false; //i值不合法
      if (p->next == NULL)
          return false; //第i-1个结点后以无结点
      LNode* DeleteNode = p->next;    //令DeleteNode指向要被删除结点
      e = DeleteNode->data;           //用e返回删除元素的值
      p->next = DeleteNode->next;     //将DeleteNode从链中断开
      free(DeleteNode);               //释放DeleteNode的存储空间
      return true;
  }
  ```

---

## 7 单链表查找操作

- 单链表不具备随机访问的特性，只能依次扫描

### 7.1 按位查找，返回第i元素(带头结点)

- 平均时间复杂度：T=O(n)

- ```cpp
  //单链表按位查找，返回第i个元素（带头结点）
  LNode* GetElem(LinkList L, int i) {
      if (i < 0)    //i值不和法
          return NULL;
      LNode* p;     //声明一个新结点p
      int SubToNode = 0;
      p = L;      //将p结点指向头结点
      while (p != NULL && SubToNode < i) {
          //遍历链表，将新结点指向所需查找结点
          p = p->next;
          SubToNode++;
      }
      return p;
  }
  ```

### 7.2 按值查找，找到数据域等于“==”e的结点(带头结点)。

- ```cpp
  //按值查找，找到数据域==e的
  LNode* LocateElem(LinkList L, int e) {
      LNode* p = L->next;
      while (p != NULL && p->data != e) {
          p = p->next;
      }
      return p;
  }
  ```

---

## 8 单链表的创建操作(带头结点)

- 分为**尾差法**，**头插法**两种。

### 8.1 尾插法

- 尾插法建立单链表：
  
  初始化单链表
  
  设置变量Length记录链表长度
  
  while循环{
  
          每次取一个数据元素e；
  
          插到尾部；
  
          Length++；
  
  }

- ```cpp
  //1.尾插法
  LinkList InsertLinkTail(LinkList& L) {
      int InsertNum;    //将输入值设为整形
      L = (LinkList)malloc(sizeof(LNode));  //建立一个单链表，即一个头结点
      LNode* OverNode, * TailNode;        //TailNode为表尾指针
      scanf_s("%d", &InsertNum);            //输入结点的值
      OverNode = (LNode*)malloc(sizeof(LNode));
      TailNode = (LNode*)malloc(sizeof(LNode));
      while (InsertNum != 9999) {
          OverNode->data = InsertNum;
          TailNode->next = OverNode;
          TailNode = OverNode;              //TailNode指向新的表尾
          scanf_s("%d", &InsertNum);
      }
      TailNode->next = NULL;            //将尾指针置空
      return L;
  }
  ```

### 8.2 头插法(可用于链表的逆置)

- 头插法建立单链表：
  
  初始化单链表
  
  while循环{
  
          每次取一个数据元素e；
  
          InsertNextNode(L);
  
  }

- ```cpp
  //2.头插法
  LinkList InsertLinkHead(LinkList& L) {
      LNode* OverNode;   
      int InsertNum;
      L = (LinkList)malloc(sizeof(LNode));  //创建头结点
      L->next = NULL;                       //初始为链表
      scanf_s("%d", &InsertNum);                       
      while (InsertNum != 9999) {
          OverNode = (LNode*)malloc(sizeof(LNode));   //为新结点分配空间
          OverNode->data = InsertNum;
          OverNode->next = L->next;
          L->next = OverNode;            //将新结点接入链表，L为头结点
          scanf_s("%d", &InsertNum);
      }
      return L;
  }
  ```

- 可用于链表的逆置

---

## 9 双链表

### 9.1 关于双链表

- 什么是双链表

- 单链表，双链表的区别
  
  - 单链表：无法逆向检索，有时候不太方便
  
  - 双链表：可进可退，存储密度较单链表更低一点

- 双链表的缺点：双链表不可随机存取，按位查找，按值查找操作都只能用遍历的方式实现。
  
  - 时间复杂度：T=O(n)

### 9.2 定义双链表

- ```cpp
  //定义一个双链表
  typedef struct DNode {
      int data;
      struct DNode *prior,*next;
  }DNode,*DLinkList;
  ```

### 9.3 初始化双链表

- ```cpp
  //初始化双链表
  bool InitDLinkList(DLinkList& L) {
      L = (DNode*)malloc(sizeof(DNode));  //分配一个头结点
      if (L == NULL)
          return false; //内存不足，分配空间失败
      L->prior = NULL;    //头结点的piror永远指向NULL
      L->next = NULL;     //头结点之后暂时还没有结点
      return true;
  }
  ```

### 9.4 双链表的插入

- ```cpp
  //双链表的插入(在结点p之后插入InsertNode结点)
  bool InsertNextDNode(DNode* p, DNode* InsertNode) {
      InsertNode->next = p->next;     //将插入结点InsertNode插入到p之后
      if(p->next!=NULL)              //如果p结点后有后继结点
          p->next->prior = InsertNode;
      InsertNode->prior = p;
      p->next = InsertNode;
  }
  ```

### 9.5 双链表的删除

- 删除p的后继结点q

- ```cpp
  //删除p结点的后继结点
  bool DeleteNextNode(DNode* p) {
      if (p == NULL)
          return false;
      DNode* OverNode = p->next;
      if (OverNode == NULL)
          return false;   //p没有后继
      p->next = OverNode->next;
      if (OverNode->next != NULL)   //判断OverNode不是最后一个结点
          OverNode->next->prior = p;
      free(OverNode);   
      return true;
  }
  ```

### 9.6 双链表的遍历

- 后向遍历
  
  ```cpp
  
  ```

- 前向遍历
  
  ```cpp
  
  ```

### 9.7 销毁双链表

- ```cpp
  //销毁双链表
  void DistoryDLinkList(DLinkList& L) {
      if (L->next != NULL)    //循环释放各个数据结点
          DeleteNextNode(L);   
      free(L);    //释放头结点
      L = NULL;    //头指针指向NULL
  }
  ```

---

## 10 循环链表

### 10.1 关于循环链表

- 循环链表的分类
  
  - 循环链表分为，循环单链表和循环双链表。

- 比较单链表与循环单链表
  
  - 单链表：从一个结点出发只能找到后续的各个结点
  
  - 双链表：从一个结点出发可以找到其他任何一个结点

### 10.2 循环单链表

- 初始化循环单链表
  
  ```cpp
  bool InitLinkList(LinkList& L) {
      L = (LNode*)malloc(sizeof(LNode));// 分配一个头结点
      if (L == NULL)    //内存不足，分配失败
          return false;
      L->next = L;   //头结点的next指向头结点
      return true;
  }
  ```

- 判断循环链表是否为空
  
  ```cpp
  //判断循环链表是否为空
  bool IsEmpty(LinkList& L) {
      if (L->next == L)
          return true;
      else
          return false;
  }
  ```

- 判断某结点p是否为表尾结点
  
  ```cpp
  bool IsTailLNode(LinkList L, LNode* p) {
      if (p->next == L)
          return true;
      else
          return false;
  }
  ```

### 10.3 循环单链表

- 初始化循环双链表
  
  ```cpp
  //初始化循环双链表
  bool InitDLinklist(DLinkList& L) {
      L = (DNode*)malloc(sizeof(DNode));
      if (L == NULL)
          return false;
      L->prior = L;
      L->next = L;
      return true;
  }
  ```

- 判断循环双链表是否为空
  
  ```cpp
  //判断循环双链表是否为空
  bool IsEmpty(DLinkList L) {
      if (L->next == L)
          return true;
      else
          return false; 
  }
  ```

---

## 11 静态链表

### 11.1 关于静态链表

- 什么是静态链表：用数组的方式实现的链表

- 比较单链表与静态链表
  
  - 单链表：各个结点在内存散落分布
  
  - 静态链表：分配一整个片连续的空间，各个结点集中安置。

- 静态链表的优缺点
  
  - 优：增删操作不需要大量移动元素
  
  - 缺：不能随机存取，只能从头结点开始依次往后查找；容量固定不可变

### 11.2 定义静态链表

- ```cpp
  #define Maxsize 10
  struct Node {
      ElemType data;
      int next;// 下一个元素的数组下标
  };
  struct Node a[Maxsize];//a为静态链表
  ```

- ```cpp
  //另一种定义方法
  typedef struct {
      int data;
      int next;
  }SLinkList[Maxsize];    
  SLinlList[Maxsize]  a;//相当于声明一个长度为Maxsize的Node型数组
  ```

### 11.3 初始化静态链表

- 把a[0]的next设为-1。

- 把空结点标记出来。(即将next设为-2)

### 11.4 查找操作

- 从头结点出发挨个往后遍历结点(T=O(n))

### 11.5 插入操作(插入位序为i结点)

- (1).找到一份空结点，存入数据元素
  
  (2).从头结点出发找到位序为i-1的结点
  
  (3).修改新结点的next
  
  (4).修改i-1号结点的next

### 11.6 删除操作

- (1).从头结点出发找到前驱结点
  
  (2).修改前驱结点的游标
  
  (3).被删除结点next设为-2

---

## 12 顺序表和链表的比较

### 12.1 逻辑结构

- 都属于线性表，都是线性结构

### 12.2 存储结构

- 顺序表
  
  - 优：支持随机存取，存储密度高
  
  - 缺：大片连续空间分配不方便，改变容量不方便

- 链表
  
  - 优：离散的小空间分配方便，改变容量方便
  
  - 缺：不可随机存取，存储密度低

### 12.3 基本操作

- 创，销，增，删，改，查
