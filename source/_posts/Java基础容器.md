---
title: Java基础容器
date: 2022-07-13 00:46:14
tags:
  - Java笔记
categories: 知识
abbrlink: containe
sticky: 90
cover: https://npm.elemecdn.com/yanqi1711-picx/img/244.webp
---
## 前言

本文转载自[学习笔记](https://mrjokersince1997.github.io/My-Notes/#/javase/%E5%AE%B9%E5%99%A8/%E5%9F%BA%E7%A1%80%E5%AE%B9%E5%99%A8?id=%e9%81%8d%e5%8e%86%e5%ae%b9%e5%99%a8)

## 基本接口

java 提供了一些基础容器类，可以用特定的方式组织、存储和操作对象数据。这些集合框架分为两大分支：Collection 接口和 Map 接口。

所有容器都定义在 java.util 文件夹内，使用时需要进行导入。

### Collection 接口
【集合】用特定的方式组织、存储和操作对象数据。有三个常用子接口 List 接口、Queue 接口、Set 接口。

Collection 接口以及所有子接口和子方法 都定义在 java.util 文件夹内，使用时需进行导入。

```java
// 修改
collection.add(1);                // 添加元素
collection.remove(1);             // 删除元素
collection.clear();               // 清除所有元素

// 查询
collection.isEmpty();             // 判断集合是否为空
collection.size();                // 返回集合元素个数
collection.contains(1):           // 判断集合中是否含有元素

// 多集合操作
collection.addAll(c2);            // 并操作，添加其他集合中元素
collection.removeAll(c2);         // 减操作，删除和其他集合共有元素
collection.retainAll(c2);         // 交操作，只保留和其他集合共有元素 
collection.equals(c2);            // 判断是否和其他集合元素相同
collection.containsAll(c2);       // 判断是否包含其它集合所有元素  

// 创建迭代器
Iterator<Integer> iter = collection.iterator();
```

### List 接口
【列表】元素有序，可以按索引操作。

```java
// 修改
list.add("data1");              // 末尾添加元素
list.add(0, "data0");           // 插入元素
list.remove(0);                 // 按索引删除元素(int)
list.remove("data");            // 按内容删除对象元素(Object)
list.remove(new Integer(3));    // 按内容删除基础类型元素
list.clear();                   // 清除所有元素
list.set(0, "data2");           // 修改元素

// 查找
list.isEmpty();                 // 判定是否为空
list.size();                    // 查询列表元素个数
list.contains("data3");         // 判定是否含有元素
list.get(1);                    // 按索引查找元素
list.indexOf("data1");          // 查询索引号：如果有返回第一个，没有返回-1
list.lastIndexOf("data1");      // 查询索引号：如果有返回最后一个，没有返回-1

// 转化
list.toString();                // 转化为字符串
list.toArray();                 // 转化为 Object[] 数组
(String [])list.toArray();      // 转化为对象数组，但不能是基础类型
```

### Queue 接口
【队列】元素有序，在队列尾插入/在队列首移除。常用 Deque 子接口。

```java
//修改
queue.offer(10);                // 队列尾插入元素，队列满返回 false
queue.peek();                   // 获取队列首元素，队列空返回 null
queue.poll();                   // 获取并移除队列首元素，队列空返回 null
queue.clear();                  // 清空元素

/* offer/peek/poll 方法可以用 add/get/remove 方法代替，但队列空/满时会抛出异常。 */

// 查找
queue.isEmpty();                 // 判定是否为空
queue.size();                    // 查询列表元素个数
queue.contains("data3");         // 判定是否含有元素

```

### Deque 接口
【双端队列】元素可以在两端进出。

```java
deque.offerFirst(e);            // 队列首添加元素 
deque.pollFirst();              // 队列首移除元素
deque.peekFirst();              // 获取队列首元素

deque.offerLast(e);                // 队列尾添加元素
deque.pollLast();               // 队列尾移除元素
deque.peekLast();               // 获取队列尾元素 

/* offer/peek/poll 方法可以用 add/get/remove 方法代替，但队列空/满时会抛出异常。 */
```

### Set 接口

【集】数据不可重复。

```java
// 修改
set.add("data");              // 添加元素
set.remove("data");           // 删除元素
set.clear();                  // 清除所有元素

// 查询
set.get(1);                   // 按序号查找元素（仅限于有序的 set 接口）
set.isEmpty();                // 判断是否为空
set.size();                   // 返回元素个数
set.contains("data");         // 判定是否含有元素
```

*HashSet 类无序，因此不支持 get 方法：获取对象必须要通过 Iterator 来遍历。*

### Collections 类

Collections 类是针对集合类的一个帮助类，他提供一系列静态方法实现各种集合操作。

1. 排序操作（主要针对List接口）

```java
Collections.swap(list, 1, 2);          // 元素交换顺序
Collections.shuffle(list);             // 元素随机排序
Collections.reverse(list);             // 元素颠倒排序
Collections.sort(list);                // 元素按大小排序，可以自定义比较顺序
Collections.rotate(list, 2);           // 元素右移指定长度
```

2. 查找和替换

```java

Collections.binarySearch(list, "data");              // 二分查找元素索引，只适用于有序集合
Collections.max(list);                               // 返回最大元素，可以自定义比较顺序
Collections.min(list);                               // 返回最小元素，可以自定义比较顺序
Collections.frequency(list, "data");                 // 返回对象出现次数

Collections.fill(list, "data");                      // 使用指定元素填充
Collections.replaceAll(list, "old", "new");          // 使用指定元素替换
```

3. 上锁（主要针对List接口）

调用 Collections 类中的 synchronizedList 方法，可以将 List 接口转换成线程安全的容器使用。

List 接口中的方法都会被添加 synchronized 锁（效率不高）。但是 iterator 方法没有加锁，如果要遍历还需要在外层加锁。

```java
List list = Collections.synchronizedList(new ArrayList());

synchronized (list) {
    Iterator i = list.iterator(); 
    while (i.hasNext())
        foo(i.next());
}
```

### Map 接口

```java
map.put("key_1",1);               // 添加键值对,已有 key 则覆盖 value
map.putIfAbsent("key_2",2);       // 添加键值对,已有 key 则不操作

map.remove("key_1");              // 删除键值对（按值）           
map.remove("key_2",2);            // 删除键值对（按键值）

map.get("key_1");                 // 获取值, key 不存在返回null
map.getOrDefault("key_2",-1);     // 获取值, key 不存在返回默认值

map.containsKey("key_1");       // 判断 key 是否存在  
map.containsValue(1);             // 判断 value 是否存在      
```

## 线性存储

### ArrayList 类

【数组序列】实现了 List 接口，内部使用 Object 数组存储：

1. 可以高效地按索引进行元素修改和查询。
2. 添加元素时动态扩容：当容量满后，ArrayList 类会新建一个 1.5 倍容量的新数组，然后将当前数组数据全部复制过去。

**ArrayList 构造方法**

```java
List<Integer> list = new ArrayList<>();              // 默认初始容量为 10
List<Integer> list = new ArrayList<>(100);           // 自定义初始容量
List<Integer> list = new ArrayList<>(queue);         // 构造时直接复制其他容器元素（可以是任何 Collection 类）

List list = new ArrayList();                         // 未指定元素类型则为 Object 类
```

### LinkedList 类

【链表序列】实现了 List 和 Deque 接口。内部使用双向链表存储：

1. 可以高效地进行元素插入和删除。
2. 容量无限。

**LinkedList 构造方法**

```java
List<String> list = new LinkedList<>();              // 创建空对象
List<String> list = new LinkedList<>(queue);         // 复制其他容器元素
```

### ArrayDeque 类

【数组双端队列】实现了 Deque 接口。内部使用 Object 数组存储（不允许存储 null 值）：

1. 可以高效进行元素查找和尾部插入取出，是用作队列、双端队列、栈甚至递归树的绝佳选择。
2. 添加元素时动态扩容：当容量满后，ArrayDeque 类会新建一个 1.5 倍容量的新数组，然后将当前数组数据全部复制过去。

**ArrayDeque 构造方法**

```java
ArrayDeque<String> queue = new ArrayDeque<>();              // 创建空对象
ArrayDeque<String> queue = new ArrayDeque<>(list);          // 复制其他容器元素
```

### PriorityQueue 类

【无界优先级队列】实现了 Queue 接口。内部使用 Object 数组存储（不允许存储 null 值）：

1. **PriorityQueue 类内会自动对元素进行排序**，是作为堆的绝佳选择。但实际在数组中并不是有序存储，而只保证队首元素是最小值：每次弹出队首元素后会自动查找剩余队列中的最小元素放到队首。
2. 添加元素时动态扩容：当容量满后，PriorityQueue 类会新建一个 1.5 倍容量的新数组，然后将当前数组数据全部复制过去。

**PriorityQueue 构造方法**

开发者在构造队列时可通过重写 compare 方法自定义排序规则。如果存储未重写 compareTo 方法的自定义对象，则必须重写 compare 方法。

```java
// 默认排序方法
PriorityQueue<Integer> queue = new PriorityQueue<Integer>();

// 自定义排序方法(Lambda 表达式)
PriorityQueue<Student> queue = new PriorityQueue<Student>((s1, s2) -> {
    if(s1.getScore() == s2.getScore()){
        return s1.getName().compareTo(s2.getName());
    }
    return s1.getScore() - s2.getScore();
});
```

## 哈希存储

### HashMap 类

【哈希表】 实现 Map 接口。底层使用散列存储：构造一个 Entry 数组，根据 key 的 hash 值将 Entry 存入指定位置。

- key 值无序且不可重复，且允许 null 作为 key 值存在。
- 发生哈希冲突时，HashMap 采用链表保存多个元素。当链表长度大于 8 时，链表自动转化为红黑树。
- 达到负载因数后，HashMap 将调用 resize 方法动态扩容：新建一个 2 倍容量的新数组复制当前数组的数据。

**HashMap 构造方法**

```java
Map<String,Integer> map = new HashMap<>();                       // 默认初始容量 16 负载因数 0.75
Map<String,Integer> map = new HashMap<>(32);                     // 自定义初始容量
Map<String,Integer> map = new HashMap<>(32, 0.5f);               // 自定义初始容量和负载因数
```

### LinkedHashMap 类

【链式哈希表】继承 HashMap 类。

1. 底层使用散列存储：构造一个 Entry 数组，根据 key 的 hash 值将 Entry 存入指定位置。
2. Entry 额外添加了引用 before & after ，使哈希表内的所有 Entry 构成一个双向链表维护 Entry 的顺序。

**LinkedHashMap 构造方法**

在默认情况下 Entry 按照插入顺序排序，可指定创建时的初始容量和负载因数。

```java
Map<String,Integer> map = new LinkedHashMap<>();                  // 默认初始容量 16 负载因数 0.75 
Map<String,Integer> map = new LinkedHashMap<>(32);                // 自定义初始容量
Map<String,Integer> map = new LinkedHashMap<>(32, 0.5f);          // 自定义初始容量和负载因数
```

Entry 也可以按照访问顺序排序：对 Entry 进行操作时会先删除再插入，将 Entry 移动到双向链表的表尾。

```java
Map<String,Integer> map = new LinkedHashMap<>(32，0.5f, true);    // 基于访问顺序排序
```

LinkedHashMap 类提供了 removeEldestEntry 方法，在使用 put 操作插入 Entry 时将自动调用此方法决定是否移除双向链表表头的 Entry：默认返回 false ，可通过重写此方法以实现 LRU 算法。

```java
// Entry 超过容量后自动删除最久未使用的 Entry
Map<String,Integer> map = new LinkedHashMap<>(capacity, 0.5f, true){
    @Override
    protected boolean removeEldestEntry(Map.Entry eldest) {  
        return size() > capacity;  
    }  
};
```

### TreeMap 类

【树表】 实现了 Map 接口。底层使用红黑树存储：Entry 按照 key 值大小插入红黑树，并动态调整红黑树高度。

**TreeMap 类方法**

TreeMap 类提供了以下专属方法使用。

```java
map.firstKey();                   // 返回最小 key
map.lastKey();                    // 返回最大 key

map.ceilingKey("10");             // 返回大于等于10的最小 Key，不存在则返回 null
map.ceilingEntry("10");           // 返回大于等于10的最小 Key 的键值对(getKey / getValue 方法)

map.floorKey("10");               // 返回小于等于10的最大 Key，不存在则返回 null
map.floorEntry("10");             // 返回小于等于10的最大 Key 的键值对
```

### Set 子类

**HashSet 类**：【散列集】基于 HashMap 类实现。

**LinkedHashSet 类**：【链式散列集】基于 LinkedHashMap 类实现。

**TreeSet 类**：【树集】基于 TreeMap 类实现。

## 元素遍历

### 遍历容器

#### Iterable 接口

是集合框架的顶级接口，被所有容器类都实现。

1. 提供 iterator 方法，用来创建一个实现了 Iterator 接口的 iterator 对象：按容器类规定的顺序实现遍历集合。
2. JDK 1.8 引入 foreach 方法遍历集合。效率更高，但不能对元素进行删除操作，否则会抛出异常。

#### Iterator 接口

提供了 hasNext、next、remove 三个方法，可以按容器类规定的顺序实现遍历集合。

### 遍历顺序

#### List / Queue 接口

- **全部方法**：按数组或链表顺序输出。

#### Map / Set 接口

- **HashSet/HashMap 类**：在返回数据时没有特别的顺序。
- **LinkedHashSet/LinkedHashMap 类**：默认按插入顺序返回数据，也可以按访问顺序返回。
- **TreeSet/TreeMap 类**：在返回数据时按 key 值从小到大排列，即按照树的中序遍历返回。

### 遍历方法

#### Collection 接口

```java
List<String> list = new ArrayList<>();

// iterator 遍历
Iterator<Integer> iter = list.iterator();
while(iter.hasNext()){              
      int num = iter.next();
      if(num < 0) iter.remove();
}

// 随机遍历（效率更高，但不能进行删除操作）
for (String str : list) {
      System.out.println(str);
}Copy to clipboardErrorCopied
```

#### Map 接口

```java
Map<String,String> map=new HashMap<String,String>();

// iterator 遍历
Iterator<Map.Entry<String, String>> iter = map.entrySet().iterator(); 
while (iter.hasNext()) { 
    Map.Entry<String, String> entry = iter.next(); 
    System.out.println(entry.getKey() + entry.getValue()); 
} 

// 随机遍历（效率更高，但不能进行删除操作）
for (Map.Entry<String, String> entry : map.entrySet()) { 
    System.out.println(entry.getKey() + entry.getValue()); 
} 

// 只遍历 key
for (String key : map.keySet()) { 
    System.out.println(key + map.get(key)); 
} 

// 只遍历 value
for (String value : map.values()) { 
    System.out.println(value); 
}Copy to clipboardErrorCopied
```

### 遍历失败

在迭代元素的时候不能通过集合的方法修改或删除元素，但可以通过迭代器的 remove 方法删除元素。

- java.util 包下面的所有的集合类都是快速失败的。直接对原容器进行修改，会抛出 ConcurrentModificationException 异常。
- java.util.concurrent 包下面的所有的集合类都是安全失败的。遍历时先对底层集合做拷贝再遍历，因此不会抛出异常。
