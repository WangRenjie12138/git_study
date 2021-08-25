## Java 容器

### 概览

容器主要包括 Collection 和 Map 两种，Collection 存储着对象的集合，而 Map 存储着键值对的映射表

#### Collection

![img](Untitled.assets/image-20191208220948084.png)

##### 1.Set

+ TreeSet：基于红黑树来实现，支持有序性操作（例如根据一个范围查找元素的操作），但是查找效率不如 HashSet，HashSet 的查找时间复杂度为 O (1)，TreeSet 则为O (logN)
+ HashSet：基于哈希表实现，支持快速查找，但不支持有序性操作。而且失去了元素的插入顺序信息，使用 Iterator 遍历 HashSet 得到的结果是不确定的
+ LinkedHashSet：具有 HashSet 的查找效率，并且内部使用双向链表维护元素的插入顺序

##### 2.List

+ ArrayList：基于动态数组实现，支持随机访问。
+ Vector：和ArrayList类似，但是它是线程安全的
+ LinkedList：基于双向链表实现，但是只能书匈奴访问，可以快速插入和删除元素。且可用于栈、队列和双向队列

##### 3.Queue

+ LinkedList：可以用它来实现双向队列
+ PriorityQueue：基于堆结构实现，可以用它来实现优先队列

#### Map

![img](Untitled.assets/image-20201101234335837.png)

+ TreeMap：基于红黑树实现
+ HashMap：基于哈希表实现
+ HashTable：和HashMap类似，是线程安全的（但是是遗留类，不用，一般用ConcurrentHashMap）
+ LinkedHashMap：使用双向链表来维护元素的顺序，顺序为插入顺序或者最近最少使用（LRU）顺序。