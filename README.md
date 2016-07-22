# do_function2
do_function2

#高级特性




#切片Slice L[0:3] 索引从0开始，直到索引3为止（不含3）
L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']
n = 0
while n < 3:
	print L[n]
	n = n + 1

r = []
n = 3
for i in range(n):    # range(n)表示0——n-1的n个数组成的list
	r.append(L[i])
r

L[0:3]    #切片
L[-1:]    #倒数第一个元素索引为-1
#后10个数：
L[-10:]
#前11-20个数：
L[10：20]
#前10个数，每两个取前1个
L[:10：2]

#Tuple也是一种list，但Tuple不可变。Tuple切片后仍为Tuple
(0,1,2,3,4,5)[:3]

#字符串'xxx'或Unicode字符串u'xxx'也可看成list，可切片操作。操作结果仍是字符串：
'ABCDEFG'[:3]

L = range(100)





#迭代
d = {'a': 1, 'b': 2, 'c': 3}    #迭代不限于有下标的list等
for key in d:
	print key

for value in d.itervalues():

for k, v in d.iteritems():

#判断是否可迭代
from collections import Iterable
isinstance('abc', Iterable)

#同时迭代索引&元素：enumerate
# enumerate把list变成 索引——元素对
for i, value in enumerate(['A', 'B', 'C']):
	print i, value




#列表生成式（list comprehension）
r = []
for i in range(1:11):
	r.append(i*i)
r

[x * x for x in range(1:11)]    #列表生成式

# for循环后面可加if判断
[x * x for x in range(1:11) if x % 2 ==0]

# 两层循环
[m + n for m in 'ABC' for n in 'XYZ']    # m + n的+号作用是连接两变量
['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']

d = {'a': 1, 'b': 2, 'c': 3}
for k, v in d.iteritems():
	print k, '=', v


d = {'x': 'A', 'y': 'B', 'z': 'C' }
[k + '=' + v for k, v in d.iteritems() ]
['y=B', 'x=A', 'z=C']

#把list中所有的字符串变成小写
L = ['Hello', 'World', 'IBM', 'Apple']
[s.lower() for s in L]

L = ['Hello', 'World', 18, 'Apple', None]
[s.lower() for s in L if isinstance(s, str) ]




#生成器（Generator)
#法1：[]改成（）
g = (x * x for x in range(10))
g
<generator object <genexpr> at 0x0000000002DA32D0>
>>>for n in g():
       print n 

#我写的蠢蠢的斐波那契数列
def fib(max):
	former = 1
	if former > 0:
		letter = 1
		max = former + letter
		former = letter
		letter = max
		print max

#斐波那契数列
def fib(max):    
	n, a, b = 0, 0, 1
	while n < max:
		print b
		a, b = b, a+b
		n = n + 1
#初看没发现max的作用，且也没赋值。fib（6）表示数列的前6个数字

#法2：yield 作用同print
def fib(max):
	n, a, b = 0, 0, 1
	while n < max:
		yield b    # yield表明这是genrator函数
		a, b = b, a+b
		n = n +1

#函数是顺序执行，遇到return语句或者最后一行函数语句就返回。
#generator的函数在每次调用next()的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行。
>>>def odd():
	print 'step 1'
	yield 1
	print 'step 2'
	yield 3
	print 'step 3'
	yield 5
>>>o = odd()
>>>o.next()
step 1
1
>>>o.next()
step 2
3
>>>o.next()
step 3
5


