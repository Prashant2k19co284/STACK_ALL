```python
class stack:
	def __init__(self):
		self.__data=[]
	def push(self,element):
		self.__data.append(element)
	def pop(self):
		if self.is_empty():
			print("The list is Empty can not pop :")
			return
		return self.__data.pop()
	def top(self):
		if self.is_empty():
			print("The list is Empty can not have the top element :")
			return 
		return self.__data[len(self.__data)-1]
	def size(self):
		return len(self.__data)
	def is_empty(self):
		return self.size()==0
```


```python
s=stack()
```


```python
s.push(5)
```


```python
s.top()
```




    5




```python
s.pop()
```




    5




```python
s.push(5)
s.push(4)
s.push(3)
s.push(2)
s.push(1)
```

# SATCK USING LINKED LIST 


```python
class Node:
    def __init__(self,data):
        self.data=data
        self.next=None
```


```python
class stack_ll:
    def __init__(self):
        self.__head=None
        self.__count=0
    def push(self,element):
        newnode=Node(element)
        newnode.next=self.__head
        self.__head=newnode
        self.__count+=1
    def pop(self):
        self.__count-=1
        data=self.__head.data
        self.__head=self.__head.next
        return data
    def top(self):
        return self.__head.data
    def size(self):
        return self.__count
    def is_empty(self):
        return self.size()==0
        
        
```


```python
s_ll=stack_ll()
```


```python
s_ll.push(1)
s_ll.push(2)
s_ll.push(3)
s_ll.push(4)
s_ll.push(5)
```


```python
s_ll.pop()
```




    5




```python
s_ll.size()
```




    4




```python
s_ll.is_empty()
```




    False




```python
s_ll.top()
```




    4



# BALANCED PARANTHESIS 


```python
def balanced(string):
    s=[]
    for ele in string:
        if ele in "[{(":
            s.append(ele)
        elif ele=="]":
            if len(s)==0 or s[-1]!="[":
                return False
            s.pop()
        elif ele=="}":
            if len(s)==0 or s[-1]!="{":
                return False
            s.pop()
        elif ele==")":
            if len(s)==0 or s[-1]!="(":
                return False
            s.pop()
    if len(s)==0:
        return True
```


```python
balanced("(a+b)")
```




    True



# REVERSE STACK 


```python
def reverse_stack(s1,s2):
    if len(s1)==0 or len(s1)==1:
        return 
    while len(s1)!=1:
        s2.append(s1[-1])
        s1.pop()
    temp=s1[-1]
    s1.pop()
    while len(s2)!=0:
        s1.append(s2[-1])
        s2.pop()
    reverse_stack(s1,s2)
    s1.append(temp)
    
```


```python
s1=[4,3,2,1]
s2=[]
reverse_stack(s1,s2)
print(s1)
print(s2)
```

    [1, 2, 3, 4]
    []
    

# REBUNDANT BRACKET CODE


```python
def R_bracket(string):
    s_1=[]
    for char in string:
        if char in "(+-*/":
            s_1.append(char)
        elif char==")":
            if len(s_1)!=0 and s_1[-1]=="(":
                s_1.pop()
                return True
            else:
                while s_1[-1]!="(":
                    s_1.pop()
    return False
```


```python
R_bracket("(a+b*+-//((a/c-d)))")
```




    True



# STOCK SPAN


```python
def stock_plan(l):
    l1=[]
    l1.append((l[0],1))
    print(1)
    i=1
    while i<len(l):
        if l[i]<l1[-1][0]:
            l1.append((l[i],1))
            print(1)
        else:
            sum=1
            while len(l1)!=0 and l[i]>l1[-1][0]:
                sum+=l1[-1][1]
                l1.pop()
            l1.append((l[i],sum))
            print(sum)
        i+=1 
```


```python
stock_plan([10,10,10,10])
```

    1
    1
    1
    1
    

# MINIMUM BRACKET REVERSIAL


```python
def minimum_reversal(string):
    if len(string)%2!=0:
        return -1
    s=[]
    for ele in string:
        if ele=="{":
            s.append(ele)
        elif len(s)!=0 and ele=="}" and s[-1]=="{":
            s.pop()
        else:
            s.append(ele)
    if len(s)==0:
        return 0
    c=0
    while len(s)!=0:
        c1=s[-1]
        s.pop()
        c2=s[-1]
        s.pop()
        if c1==c2:
            c+=1
        else:
            c+=2
    return c
```


```python
minimum_reversal("{{")
```




    1


