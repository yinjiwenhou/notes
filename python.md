### python 面试题整理 [ https://blog.csdn.net/javahuazaili/article/details/87927181 ]

* 一行代码实现1—100之和
    ```python
    # use reduce
    reduce(lambda x, y: x + y, xrange(1, 101))

    # use sum
    sum(range(1, 101))
    ```

* 如何在一个函数内部修改全局变量
    ```python
    global VAR
    def foo():
        global VAR
        VAR = VAR + 1
    ```

* 列出5个python标准库
    ```python
    os, sys, time, datetime, re, math, logging
    ```

* 字典如何删除键和合并两个字典
    ```python
    d1 = {"a": "aaa", "b": "bbb"}
    d2 = {"c": "ccc"}
    del d1["a"]
    d1.update(d2)
    ```

* 谈下python的GIL

    全局解释器锁，同一个进程内如果多个线程运行，一个线程在运行python程序的时候会通过加锁霸占python解释器， 是得该进程内的其他线程无法运行。
    需等待该线程执行完成之后才能运行。如果线程运行过程中遇到耗时操作，则解释器锁解开，是其他线程运行。
    所以在多线程中，线程的运行还是有先后顺序的，并不是同时执行的。

* python实现列表去重的方法
    ```python
    l = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
    list(set(l))

    {key: 1 for key in l}.keys()
    ```

* fun(*args,**kwargs)中的*args,**kwargs什么意思？

    两者都是用于函数定义。

    *args: 不定长度位置参数

    **kwargs: 不定长度关键字参数

* python2和python3的range（100）的区别

    python2: 得到真实的列表。
    python3：generate对象，通过循环迭代或是next函数获取。

* 一句话解释什么样的语言能够用装饰器?

    函数是一等公民的编程语言（可以作为函数参数，可以作为函数返回值， 能赋值给其他变量）

* python内建数据类型有哪些
    ```python
    int, float, bool, str, tuple, list, dict, set
    ```

* 简述面向对象中__new__和__init__区别

    __new__: 至少有一个cls参数，代表当前类。必须要有返回值，返回实例化出来的实例。新创建实例时调用，在__init__之前执行，
    
    __init__: 至少有一个self参数，就是__new__中返回的实例，还可以有其他的参数用于初始化实例。不需要返回值。
    如果__new__中返回的就是当前类的实例，__init__会被自动调用。

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

* &#60;div class="nam">中国&#60;/div>，用正则匹配出标签里面的内容（“中国”），其中class的类名是不确定的
    ```python
    import re
    re.findall(r'<div class=”.*”>(.*?)</div>', a) # ['中国']
    ```

* python中断言方法举例
    ```python
    assert Ture
    assert a == b
    ```

* 数据表student有id,name,score,city字段，其中name中的名字可有重复，需要消除重复行,请写sql语句
    ```sql
    select distinct name from student;
    ```

* 10个Linux常用命令
    ```bash
    cd, mkdir, mv, touch, chown, chmod, ps, cat, tail, wc, grep, sed, awk
    ```

* python2和python3区别？列举5个
    1. print 等语句全部成了函数
    2. range 函数的返回值从列表变为的生成器表达式
    3. python3中新增了 **nonlocal** 关键字
    4. 捕获异常不能再使用catch Exception， e， 而是使用catch Exception as e
    5. reduce函数不再是buildin，移到functools中
    6. python2使用ascii编码，python3使用unicode编码

* 列出python中可变数据类型和不可变数据类型，并简述原理
    1. 不可变类型： tuple， str， int， float
    2. 可变类型： list， dict

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
    d = {"name":"zs","age":18,"city":"深圳","tel":"1362626627"}
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
    a = "not 404 found 张三 99 深圳"
    re.sub(r'[a-zA-Z0-9]+\s', '', a)
    ```

* filter方法求出列表所有奇数并构造新列表，a =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    ```python
    a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    b = filter(lambda x: x % 2 == 1, a) # filter 接受的函数只需返回True/False
    ```

* 列表推导式求列表所有奇数并构造新列表，a =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    ```python
    a =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    b = [ item for item in a if item % 2 == 1]
    ```

* 正则re.complie作用
    ```python
    import re
    re.complite() # 编译正则表达式，得到正则表达式对象
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
    s, o = commands.getstatusoutput(cmd)
    os.system(cmd)
    ```

* log日志中，我们需要用时间戳记录error,warning等的发生时间，请用datetime模块打印当前时间戳 “2018-04-01 11:38:54”
    ```python
    import datetime
    datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')
    ```

* 数据库优化查询方法
    
    外键， 索引，联合查询， 选择特定字符

* 请列出你会的任意一种统计图（条形图、折线图等）绘制的开源库，第三方也行
    ```python
    import matplotlib
    import pychart
    ```

* 写一段自定义异常代码
    ```python
    class MyException(Exception):
        def __str__():
            return "my exception."
    ```

* 正则表达式匹配中，（.）和（.*?）匹配区别？
    
    (.*): 贪婪匹配， 会把满足正则表达式的尽可能多的往后匹配

    (.*?): 非贪婪匹配，会把满足正则表达式的尽可能少的匹配
    ```python
    import re
    s = '<p>哈哈</p><p>呵呵</p>'
    re.findall(r'<p>(.*)</p>', s) # ['哈哈</p><p>呵呵']
    re.findall(r'<p>(.*?)</p>', s) # ['哈哈', '呵呵']
    ```

* 简述Django的orm

    实现了数据模型和数据库的解耦， 通过简单的配置就能更换数据库。
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
    b = [6, 5, 4, 100]
    # 同步循环序列a， b。 长度不一致时以较短的为主
    for item_a, item_b in zip(a, b): #zip函数返回元组
        print(item_a + item_b)
    # 7, 7, 7
    ```

* a=”张明 98分”，用re.sub，将98替换为100
    ```python
    import re
    a = "张明 98分"
    re.sub(r'98', '100', a)
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
    a_byte = bytes(a, 'utf-8') # a = b'hello'
    b_byte = bytes(b, 'utf-8') # b = "你好".encode()
    ```

* [1,2,3]+[4,5,6]的结果是多少？
    ```python
    [1,2,3]+[4,5,6] # [1,2,3,4,5,6]
    ```

* 提高python运行效率的方法
    1. 使用生成器，可以节约内存；
    2. 循环代码优化， 避免过多重复代码执行
    3. 核心模块用Cython， PyPy
    4. 多线程，多进程，协程
    5. 多个if elif条件判断，把最有可能的情况放在最前面

* 简述mysql和redis区别
    1. mysql是关系型数据库， redis是非关系型数据库
    2. redis是内存型的数据库，访问速度更快，对硬件要求更高， mysql存储在磁盘上，访问速度稍慢。

* 遇到bug如何处理
    1. 分析日志（logging模块记录的log文件）
    2. 使用print打印想看的变量进行调试
    3. 使用IDE的debug模式执行程序，单步执行跟踪

* 正则匹配，匹配日期2018-03-20
    
    

    ```python
    import re
    url='https://sycm.taobao.com/bda/tradinganaly/overview/get_summary.json?dateRange=2018-03-20%7C2018-03-20&dateType=recent1&device=1&token=ff25b109b&_=1521595613462'
    re_str = "2018-03-20"
    regx = re.complite(re_str)
    re.match(regx, url)
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

    ```python
    test_list = [2,3,5,4,9,6]
    s_list = []
    def get_min(l):
        a = min(l)
        l.remove(a)
        a_list.append(a)

        if len(l) > 0:
            get_min(l)
    get_min(test_list)
    print(s_list)
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
    ```python
    a = '%.03f' % 1.3335 # 1.335
    b = round(float(a), 2) # 1.33
    b = round(float(a) 1) # 1.3
    ```

* 求三个方法打印结果

    ```python
    def fn(k, v, dic={}):
        dic[k] = v
        print(dic)

    fn("one", 1)
    fn("two", 2)
    fn("three", 3, {})
    ```

    ```bash
    {"one": 1}
    {"one": 1, "two": 2}
    {"three": 3}
    ```

* 列出常见的状态码和意义
    * 200 ok
    * 400 bad request
    * 401 unauthoritied
    * 404 not found
    * 403 permission denied.
    * 503 server error

* 分别从前端、后端、数据库阐述web项目的性能优化
    1. 前端：减少HTTP请求；按路由拆分页面，不要一次性加载所有的js
    2. 后端：异步处理耗时操作；缓存变化少，请求次数多的数据；
    3. 数据库：使用内存型数据库缓存session等经常访问的数据；建立索引，外键

* 使用pop和del删除字典中的”name”字段，dic={“name”:”zs”,”age”:18}
    ```python
    dic = {"name":"zs","age":18}
    dic.pop("name")
    del dic["name"]
    ```

* 列出常见MYSQL数据存储引擎
    ```python
    InnoDB， MyISAM， MEMORY
    ```

* 计算代码运行结果，zip函数历史文章已经说了，得出[(“a”,1),(“b”,2)，(“c”,3),(“d”,4),(“e”,5)]
    ```python
    a = "abcde"
    b = [1, 2, 3, 4, 5]
    [x, y for x, y in zip(a, b)]
    ```

* 简述同源策略
    
    1. 协议相同
    2. 域名相同
    3. 端口相同

* 简述cookie和session的区别
    1. cookie: 存储在浏览器端，安全性比session差。
    2. session：存储在server端，session_id以cookie的形式保存在客户端

* 简述多线程、多进程

    进程：操作系统进行资源分配和调度的基本单位，多个进程之间相互独立；稳定性好，如果一个进程崩溃，其他进程不受影响；但是进程消耗资源大，开启的进程数有限；

    线程：CPU进行资源分配和调度的基本单位，线程是进程的一部分。是比进程更小的能独立运行的基本单位。一个进程下的多个线程可以共享该进程的所有资源。

    1. 多线程：进程内包含主线程及其他子线程，但是由于存在GIL，每个CPU时间只能有一个线程执行，各个线程之间可以相互通信及共享数据。适用于IO密集型。
    2. 多进程：每个进程抖拥有独立的进程id及内存空间，不能共享数据。适用于CPU密集型。

* 简述any()和all()方法
    * any()： 序列中有一个为True及返回True
    * all()：系列中全部为True，才返回True

* IOError、AttributeError、ImportError、IndentationError、IndexError、KeyError、SyntaxError、NameError分别代表什么异常
    * IOError：输入输出异常
    * AttributeError：试图访问一个对象没有的属性
    * ImportError： 导入模块或包异常
    * IndentationError： 语法错误，代码没有正确对齐
    * IndexError：下标超过索引
    * KeyError： 字典中不存在key的异常
    * SyntaxError：语法错误，不能执行
    * NameError：使用一个还未赋予对象的变量

* python中copy和deepcopy区别

    copy():浅拷贝，不可变数据拷贝值，可变数据拷贝内存索引
    deepcopy(): 深拷贝，可变或是不可变数据都拷贝值

* 列出几种魔法方法并简要介绍用途
    
    1. __init__:对象初始化方法
    2. __new__: 创建对象的时候调用的方法
    3. __del__: 删除对象的时候调用的方法
    4. __call__: 直接将实例作为方法调用的时候调用的方法
    

* C:\Users\ry-wu.junya\Desktop>python 1.py 22 33命令行启动程序并传参，print(sys.argv)会输出什么数据？
    ```bash
    ['1.py', '22', '33']
    ```

* 将[i for i in range(3)]改成生成器
    ```python
    (i for i in range(3))
    ```

* a = “  hehheh  “,去除首尾空格
    ```python
    a = "  hehheh  "
    a.strip()
    ```

* 举例sort和sorted对列表排序，list=[0,-1,3,-10,5,9]
    ```python
    list=[0,-1,3,-10,5,9]
    sorted(list) # 返回排序之后的列表
    list.sort() # 针对list本身排序
    ```

* 对list排序foo = [-5,8,0,4,9,-4,-20,-2,8,2,-4],使用lambda函数从小到大排序
    ```python
    foo = [-5,8,0,4,9,-4,-20,-2,8,2,-4]
    sorted(foo, key=lambda x: x)
    ```

* 使用lambda函数对list排序foo = [-5,8,0,4,9,-4,-20,-2,8,2,-4]，输出结果为[0,2,4,8,8,9,-2,-4,-4,-5,-20]，正数从小到大，负数从大到小
    ```python
    foo = [-5,8,0,4,9,-4,-20,-2,8,2,-4]
    sorted(foo, key=lambda x: (x < 0, abs(x))) # key 可以是元组，当元组第一个值相同的时候使用第二值为依据，对第一个值相同的数据进行局部排序；
    ```

* 列表嵌套字典的排序，分别根据年龄和姓名排序
    ```python
    foo = [{"name":"zs","age":19},{"name":"ll","age":54},{"name":"wa","age":17},{"name":"df","age":23}]
    # sort by name 
    sorted(foo, key=lambda item: item["name"])
    # sort by age
    sorted(foo, key=lambda item: item["age"])
    ```

* 列表嵌套元组，分别按字母和数字排序
    ```python
    foo = [("zs",19),("ll",54),("wa",17),("df",23)]
    # sort by name 
    sorted(foo, key=lambda item: item[0])
    # sort by age
    sorted(foo, key=lambda item: item[1])
    ```

* 列表嵌套列表排序，年龄数字相同怎么办？
    ```python
    foo = [["zs",19],["ll",23],["wa",23],["df",23]]
    sorted(foo, key=lambda x: (x[1], x[0]))
    # key 可以是元组，当第一个值相同时按第二个元素进行排序
    ```

* 根据键对字典排序（方法一，zip函数）
    ```python
    dic = {"name": "abc", "sex": "man", "city": "xa"}
    foo = zip(dic.keys(), dic.values())
    sorted_foo = sorted(foo, key=lambda x: x[0])
    sorted_dic = {key: dic[key] for key in sorted_foo}
    ```

* 据键对字典排序（方法二,不用zip)
    ```python
    dic = {"name": "abc", "sex": "man", "city": "xa"}
    sorted(dic.items(), key=lambda x: x[0])
    ```

* 列表推导式、字典推导式、生成器
    ```python
    foo = [1, 2, 3, 4]
    # 列表推导式
    [item^^2 for item in foo]
    # 字典推导式
    {item: item*2 for item in foo}
    # 生成器
    (item for item in foo)
    ```

* 最后出一道检验题目，根据字符串长度排序，看排序是否灵活运用
    ```python
    foo = ["aa", "b", "ccc"]
    sorted(foo, key=lambda x: len(x)) # 返回值为排序后的列表
    foo.sort(key=len) # 在foo自身上排序，无返回值
    ```

* 举例说明SQL注入和解决办法
    ```python
    # todo
    ```

* s=”info:xiaoZhang 33 shandong”,用正则切分字符串输出[‘info’, ‘xiaoZhang’, ‘33’, ‘shandong’]
    ```python
    import re
    s = "info:xiaoZhang 33 shandong"
    re.split("\s|:",s)
    ```

* 正则匹配以163.com结尾的邮箱
    ```python
    import re
    email = "123123abc@163.com"
    re.match(r'@163.com$', email)
    ```

* 递归求和
    ```python
    def get_sum(x):
        if x > 0:
            res = x + get_sum(x-1)
        else:
            res = 0
        return res
    ```

* python字典和json字符串相互转化方法
    ```python
    import json
    dic = json.load(fp)
    dic = json.loads(string)

    jso = json.dump(fp)
    jso = json.dumps(dic)
    ```

* MyISAM 与 InnoDB 区别：
    ```python
    # todo
    ```

* 统计字符串中某字符出现次数
    ```python
    foo = "abcdefadees"
    foo.count('a')
    ```

* 字符串转化大小写
    ```python
    foo = 'abcABC'
    foo.upper()
    foo.lower()
    ```

* 用两种方法去空格
    ```python
    foo = "abc def ccc"
    # case 1
    foo.replace(" ", "")
    # case 2
    l = foo.split("")
    "".join(l)
    ```

* 正则匹配不是以4和7结尾的手机号
    ```python
    import re
    email = "aaa123bbb@163.com"
    ret = re.match(r'[\w]*@163.com$', email)
    print(ret.group())
    ```

* 简述python引用计数机制

    当有一个变量保存了对象的引用，这个对象的引用计数就会加一。

* int(“1.4”),int(1.4)输出结果？
    ```python
    int("1.4") # ValueError
    int(1.4) # 1
    ```

* 列举3条以上PEP8编码规范
    * 变量名以小写字符命名， 并以下划线分割
    * 类名首字母大写
    * 以4个空格缩进

* 正则表达式匹配第一个URL
    ```python
    import re
    foo = '<img title="aaa" class="aligncenter lazyloaded" style="box-sizing: border-box !important;word-wrap: break-word !important;width: 99%;visibility: visible !important;height: auto !important;box-shadow: rgb(170, 170, 170) 0em 0em 1em 0px;border-radius: 6px;" alt="110道python面试题，你会几个？" src="https://www.01hai.com/wp-content/uploads/2019/08/01hai8-1566225813.jpg" data-src="https://www.01hai.com/wp-content/uploads/2019/08/01hai8-1566225813.jpg">'
    re.findall(r'https://.*?\.jpg', foo)
    res = re.search(r'https://.*?\.jpg', foo)
    res.group()
    ```
    

* 正则匹配中文
    ```python
    import re
    foo = '你好 hello 世界 world'
    pattern = re.compile(r'[\u4e00-\u9fa5]+')
    res = pattern.findall(foo)
    print(res)
    ```

* 简述乐观锁和悲观锁
    
    悲观锁：每次拿数据的时候都会认为别人会修改数据，所以每次那数据的时候都上锁。

    乐观锁：每次拿数据的时候都认为别人不会修改数据，所以不上锁。但是在更新数据的时候会判断下在此期间别人有没有更新数据。

* r、r+、rb、rb+文件打开模式区别
    ```bash
    r: 只读模式（文件的指针在文件的开头）
    r+: 读，追加写（文件的指针在文件的开头）
    rb: 二进制方式打开，只读（文件的指针在文件的开头）
    rb+: 二进制方式读，追加写（文件的指针在文件的开头）
    ```

* Linux命令重定向 > 和 >>
    ```bash
    >: 覆盖写
    >>： 追加写，追加到尾部
    ```

* 正则表达式匹配出 ```<html><h1>www.itcast.cn</h1></html>```
    ```python
    import re
    foo = '<html><h1>www.itcast.cn</h1></html>'
    ret = re.match(r'<(\w*)><(\w*)>.*?</\2></\1>', foo)
    res.group()
    ```

* python传参数是传值还是传址？

    可变数据是传址，不可变数据是传值

* 求两个列表的交集、差集、并集
    ```python
    foo = ['a', 'b', 'c']
    bar = ['b', 'c', 'e']

    # 交集
    a = [item for item in foo if item in bar]

    # 差集
    b = [item for item in foo if item not in bar]
    b = [item for item in bar if item not in foo]

    # 并集
    foo + [item for item in bar if item not in foo]
    ```

* 生成0-100的随机数
    ```python
    import random
    random.randint(1, 100)
    random.choice(range(1, 101))
    ```

* lambda匿名函数好处

    结合高阶函数，定义简单的函数体

* 常见的网络传输协议

    tcp, udp, http, sftp, smtp

* 单引号、双引号、三引号用法

    单引号，双引号用于定义字符串
    三引号可以分开多行书写， 常用于定义文档；

* python垃圾回收机制

    垃圾回收以引用计数为主， 标记-清除和分代清除为辅， 其中标记-清除和分代清除为了处理循环引用的难题。
    
    当一个变量保存了一个对象的引用时， 此对象的引用对象计数加1。 当使用del删除变量的引用时，此对象的引用计数减1. 一个对象引用计数为0后会将回收该对象；

* HTTP请求中get和post区别

    get用于请求数据，请求参数可以跟在url里面。安全性比post差。
    post用于向服务器提交数据，提交的数据在请求的data字段中

* python正则中search和match
    ```python
    import re
    ret = re.match # 只检测字符串开头是否匹配
    ret = re.search # 会在整个字符串中查找，检测到第一个匹配到的数据

    ret.group() # 匹配结果都需要使用group

    # 返回所有满足匹配条件的结果，放在列表里
    re.findall("a", "a aa ab ac") # ['a', 'a', 'a', 'a', 'a']

    # 先按'a'分割得到''和'bcd',在对''和'bcd'分别按'b'分割
    print(re.split('[ab]', 'abcd')) # ['', '', 'cd']

    # 将数字替换成'H'，参数1表示只替换1个
    ret = re.sub('\d', 'H', 'eva3egon4yuan4', 1) #evaHegon4yuan4
    
    # 将数字替换成'H'，返回元组(替换的结果,替换了多少次)
    ret = re.subn('\d', 'H', 'eva3egon4yuan4') # ('evaHegonHyuanH', 3)

    # 将正则表达式编译成为一个 正则表达式对象
    pattern = re.compile('\d{3}')

    # finditer返回一个存放匹配结果的迭代器
    ret = re.finditer('\d', 'ds3sy4784a')   
    ```
