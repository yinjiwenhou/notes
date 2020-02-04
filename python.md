### python 面试题整理 [ https://blog.csdn.net/javahuazaili/article/details/87927181 ]

* 一行代码实现1—100之和
    ```python
    reduce(lambda x, y: x + y, xrange(1, 101))
    sum(range(1, 101))
    ```

* 如何在一个函数内部修改全局变量
    ```python
    global VAR
    def foo():
        global VAR
        VAR = VAR+1
    ```

* 列出5个python标准库
    ```python
    os, sys, time, re, functools, math
    ```

* 字典如何删除键和合并两个字典
    ```python
    d1 = {"a": "aaa", "b": "bbb"}
    d2 = {"c": "ccc"}
    del d1["a"]
    d1.update(d2)
    ```

* 谈下python的GIL

    全局解释器锁，同一个进程内，在一个单元时间内，解释器只能执行一个线程。

* python实现列表去重的方法
    ```python
    l = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
    list(set(l))

    {key: 1 for key in l}.keys()
    ```

* fun(*args,**kwargs)中的*args,**kwargs什么意思？

    *args: 不定长度位置参数

    **kwargs: 不定长度关键字参数

* python2和python3的range（100）的区别

    python2: 得到真实的列表
    python3：generate对象，通过循环迭代或是next函数获取

* 一句话解释什么样的语言能够用装饰器?

    函数是一等公民的编程语言（可以作为函数参数，可以作为函数返回值， 能赋值给其他变量）

* python内建数据类型有哪些
    ```python
    int, float, bool, str, function, 
    ```

* 简述面向对象中__new__和__init__区别
    __new__: 新创建实例时调用，在__init__之前执行，
    __init__: 接受创建新实例时需要的参数。

* 简述with方法打开处理文件帮我我们做了什么？
    with处理上下文管理器，帮助我们在程序进入上下文管理器时创建对象，在推出上下文管理器的时候销毁对象。

    实现上下文管理器的方式：
    1. 实现__entrance__, __exit__方法
    2. functools模块中的contextmanager装饰器

* 列表[1,2,3,4,5],请使用map()函数输出[1,4,9,16,25]，并使用列表推导式提取出大于10的数，最终输出[16,25]
    ```python
    l = [1,2,3,4,5]
    list(map(lambda x: x**2, l))

    [item for item in map(lambda x: x**2, l) if item > 15]
    ```

* python中生成随机整数、随机小数、0—1之间小数方法
    ```python
    import random
    random.randint(1, 100) # 1-100之前随机的整数
    random。random() # [0. 1) 之间随机的小数
    # 随机小数？
    ```

* 避免转义给字符串加哪个字母表示原始字符串？
    ```python
    r''
    ```

* <div class="nam">中国</div>，用正则匹配出标签里面的内容（“中国”），其中class的类名是不确定的
    ```python
    import re
    # todo
    ```

* python中断言方法举例
    ```python
    assert Ture
    assert a == b
    ```

* 数据表student有id,name,score,city字段，其中name中的名字可有重复，需要消除重复行,请写sql语句
    ```sql
    # todo
    ```

* 10个Linux常用命令
    ```bash
    cd, mkdir, mv, touch, chown, chmod, ps, cat, tail, wc, grep, sed, awk
    ```

* python2和python3区别？列举5个
    1. print 等语句全部成了函数
    2. range 函数的返回值从列表变为的生成器表达式
    3. python3中新增了**nonlocal**关键字
    4. 捕获异常不能再使用catch Exception， e， 而是使用catch Exception as e
    5. reduce函数不再是buildin，移到functools中

* 列出python中可变数据类型和不可变数据类型，并简述原理
    1. 不可变类型： tuple， str， int， float
    2. 可变类型： list， set

* s = “ajldjlajfdljfddd”，去重并从小到大排序输出”adfjl”
    ```python
    s = “ajldjlajfdljfddd”
    s_list = list(s)
    s_set = set(s_list)
    _s = "".join(sorted(s_set))
    ```

* 用lambda函数实现两个数相乘
    ```python
    lambda x, y: x * y
    ```

* 字典根据键从小到大排序dict={“name”:”zs”,”age”:18,”city”:”深圳”,”tel”:”1362626627”}
    ```python
    {key: d[key] for key in sorted(d, key=lambda x: x[0])}
    ```

* 利用collections库的Counter方法统计字符串每个单词出现的次数”kjalfj;ldsjafl;hdsllfdhg;lahfbl;hl;ahlf;h”
    ```python
    from collections import Counter
    s = "kjalfj;ldsjafl;hdsllfdhg;lahfbl;hl;ahlf;h"
    dict(Counter(s))
    ```

* 字符串a = “not 404 found 张三 99 深圳”，每个词中间是空格，用正则过滤掉英文和数字，最终输出”张三  深圳”
    ```python
    import re
    a = “not 404 found 张三 99 深圳”

    ```

* filter方法求出列表所有奇数并构造新列表，a =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    ```python
    a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    b = filter(lambda x: x % 2 == 1, a)
    ```

* 列表推导式求列表所有奇数并构造新列表，a =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    ```python
    a =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    b = [ item for item in a if item % 2 == 1]
    ```

* 正则re.complie作用
    ```python
    import re
    re.complite() # 编译正则表达式
    ```

* a=（1，）b=(1)，c=(“1”) 分别是什么类型的数据？
    ```python
    a=(1，) #tuple
    b=(1) # int
    c=("1") # str
    ```

* 两个列表[1,5,7,9]和[2,2,6,8]合并为[1,2,2,3,6,7,8,9]
    ```python
    a = [1,5,7,9]
    b = [2,2,6,8]
    c = a.extend(b).sort()
    ```

* 用python删除文件和用linux命令删除文件方法
    ```python
    file_path = ''
    # os module
    import os
    os.remove(file_path)

    # linux
    import commands
    cmd = 'rm -rf %s' % file_path
    s, o = commands.getsatusoutput(cmd)
    os.system(cmd)
    ```

* log日志中，我们需要用时间戳记录error,warning等的发生时间，请用datetime模块打印当前时间戳 “2018-04-01 11:38:54”
    ```python
    import datetime
    # todo
    ```

* 数据库优化查询方法
    ```sql
    # todo
    ```

* 请列出你会的任意一种统计图（条形图、折线图等）绘制的开源库，第三方也行
    ```python
    import mathplotlib
    ```

* 写一段自定义异常代码
    ```python
    class MyException(Exception):
        def __str__():
            return "my exception."
    ```

* 正则表达式匹配中，（.）和（.?）匹配区别？
    ```python
    # todo
    ```

* 简述Django的orm
    1. orm 关系对象映射；
    2. python一个类（继承自model）对应数据库一张表；
    3. 上述类的一个实例对应数据表中一条数据记录。

* [[1,2],[3,4],[5,6]]一行代码展开该列表，得出[1,2,3,4,5,6]
    ```python
    a = [[1,2],[3,4],[5,6]]
    [item for l in a for item in l]
    ```

* x=”abc”,y=”def”,z=[“d”,”e”,”f”],分别求出x.join(y)和x.join(z)返回的结果
    ```python
    x = "abc"
    y = "def"
    z = ["d", "e", "f"]

    x.join(y) # "dabceabcf"
    x.join(z) # "dabceabcf"
    ```

* 举例说明异常模块中try except else finally的相关意义
    ```python
    try: # 执行产生异常的代码
        pass
    except Exception: # 捕获异常并处理
        pass
    else: # 如果不产生异常，正常的处理流程
        pass
    finally: # 无论是否产生异常，最后都会执行的部分
        pass
    ```

* python中交换两个数值
    ```python
    x, y = y, x
    ```

* 举例说明zip（）函数用法
    ```python
    a = [1, 2, 3]
    b = [6, 5, 4]
    for item_a, item_b in zip(a, b): # 同步循环序列a， b
        print(item_a + item_b)
    # 7, 7, 7
    ```

* a=”张明 98分”，用re.sub，将98替换为100
    ```python
    import re
    # todo
    ```

* 写5条常用sql语句
    ```sql
    use mydatabase;
    create table student(var name, Integer age);
    insert into student("tony", 18)
    select name from student where age > 20;
    update student set age = 19 where name = 'tony';
    delete from student where name like '%tom%';
    drop table if exists studet;
    ```

* a=”hello”和b=”你好”编码成bytes类型
    ```python
    a="hello"
    b="你好"
    a_byte = bytes(a, 'utf-8')
    b_byte = bytes(b, 'utf-8')
    ```

* [1,2,3]+[4,5,6]的结果是多少？
    ```python
    [1,2,3]+[4,5,6] # [1,2,3,4,5,6]
    ```

* 提高python运行效率的方法
    1. #todo

* 简述mysql和redis区别
    1. mysql是关系型数据库， redis是非关系型数据库
    2. redis是内存型的数据库，访问速度更快，对硬件要求更高

* 遇到bug如何处理
    1. 分析日志（logging模块记录的log文件）
    2. 使用print打印想看的变量进行调试
    3. 使用IDE的debug模式执行程序，单步执行跟踪

* 正则匹配，匹配日期2018-03-20
    
    url=’https://sycm.taobao.com/bda/tradinganaly/overview/get_summary.json?dateRange=2018-03-20%7C2018-03-20&dateType=recent1&device=1&token=ff25b109b&_=1521595613462‘

    ```python
    import re
    re_str = "[0-9]{4}-[0-9]{2}-[0-9]{2}"
    ```

* list=[2,3,5,4,9,6]，从小到大排序，不许用sort，输出[2,3,4,5,6,9]
    ```python
    test_list = [2,3,5,4,9,6]
    for i in range(len(test_list)):
        for j in range(len(test_list[i+1:])):
            if test_list[i] > test_list[j+i+1]:
                test_list[i], test_list[j+i+1] = test_list[j+i+1], test_list[i]
    print(test_list)
    ```

* 写一个单例模式
    ```python
    class Single(object):
        def __new__(cls):
            if "_instance" not in cls.__dict__.keys():
                cls.__dict__["_instance"] = cls()
            return cls.__dict__.get("_instance")
    ```
    ```python
    class Single(object):
        pass
    single = Single()
    ```

* 保留两位小数

    题目本身只有a=”%.03f”%1.3335,让计算a的结果，为了扩充保留小数的思路，提供round方法（数值，保留位数）

* 求三个方法打印结果

    **todo**

* 列出常见的状态码和意义
    * 200 ok
    * 404 not found
    * 403 permission denied.
    * 503 server error

* 分别从前端、后端、数据库阐述web项目的性能优化
    1. 前端：按路由拆分页面，不要一次性加载所有的js
    2. 后端：异步处理耗时操作
    3. 数据库：使用内存型数据库缓存session等经常访问的数据

* 使用pop和del删除字典中的”name”字段，dic={“name”:”zs”,”age”:18}
    ```python
    dic = {"name":"zs","age":18}
    dic.pop("name")
    del dic["name"]
    ```

* 列出常见MYSQL数据存储引擎
    ```python
    PyMysql
    ```

* 计算代码运行结果，zip函数历史文章已经说了，得出[(“a”,1),(“b”,2)，(“c”,3),(“d”,4),(“e”,5)]
    ```python
    a = "abcde"
    b = [1, 2, 3, 4, 5]
    [x, y for x, y in zip(a, b)]
    ```

* 简述同源策略
    
    **todo**

* 简述cookie和session的区别
    1. cookie: 存储在浏览器端
    2. session：存储在server端
63、简述多线程、多进程
64、简述any()和all()方法
65、IOError、AttributeError、ImportError、IndentationError、IndexError、KeyError、SyntaxError、NameError分别代表什么异常
66、python中copy和deepcopy区别
67、列出几种魔法方法并简要介绍用途
68、C:\Users\ry-wu.junya\Desktop>python 1.py 22 33命令行启动程序并传参，print(sys.argv)会输出什么数据？
69、请将[i for i in range(3)]改成生成器
70、a = “  hehheh  “,去除收尾空格
71、举例sort和sorted对列表排序，list=[0,-1,3,-10,5,9]
72、对list排序foo = [-5,8,0,4,9,-4,-20,-2,8,2,-4],使用lambda函数从小到大排序
73、使用lambda函数对list排序foo = [-5,8,0,4,9,-4,-20,-2,8,2,-4]，输出结果为
[0,2,4,8,8,9,-2,-4,-4,-5,-20]，正数从小到大，负数从大到小
74、列表嵌套字典的排序，分别根据年龄和姓名排序
75、列表嵌套元组，分别按字母和数字排序
76、列表嵌套列表排序，年龄数字相同怎么办？
77、根据键对字典排序（方法一，zip函数）
78、根据键对字典排序（方法二,不用zip)
79、列表推导式、字典推导式、生成器
80、最后出一道检验题目，根据字符串长度排序，看排序是否灵活运用
81、举例说明SQL注入和解决办法
82、s=”info:xiaoZhang 33 shandong”,用正则切分字符串输出[‘info’, ‘xiaoZhang’, ‘33’, ‘shandong’]
83、正则匹配以163.com结尾的邮箱
84、递归求和
85、python字典和json字符串相互转化方法
86、MyISAM 与 InnoDB 区别：
87、统计字符串中某字符出现次数
88、字符串转化大小写
89、用两种方法去空格
90、正则匹配不是以4和7结尾的手机号
91、简述python引用计数机制

92、int(“1.4”),int(1.4)输出结果？
93、列举3条以上PEP8编码规范

94、正则表达式匹配第一个URL

95、正则匹配中文

96、简述乐观锁和悲观锁

97、r、r+、rb、rb+文件打开模式区别

98、Linux命令重定向 > 和 >>

99、正则表达式匹配出 <html><h1>www.itcast.cn</h1></html>

100、python传参数是传值还是传址？


101、求两个列表的交集、差集、并集
102、生成0-100的随机数
103、lambda匿名函数好处
104、常见的网络传输协议
105、单引号、双引号、三引号用法
106、python垃圾回收机制
107、HTTP请求中get和post区别
108、python中读取Excel文件的方法
109、简述多线程、多进程
110、python正则中search和match