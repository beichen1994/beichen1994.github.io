---
title: 爬虫之5BeautifulSoup
date: 2020-02-07 23:52:31
tags:
- 爬虫
categories: 
- Computer
---


# BeautifulSoup
| 解析器	| 使用方法	| 优势	| 劣势 |
|--| -- |-- |-- |
| Python标准库 |	BeautifulSoup(markup, "html.parser")	| Python的内置标准库、执行速度适中 、文档容错能力强 | Python 2.7.3 or 3.2.2)前的版本中文容错能力差|
| lxml HTML 解析器	| BeautifulSoup(markup, "lxml")	| 速度快、文档容错能力强 | 需要安装C语言库 |
| lxml XML 解析器	| BeautifulSoup(markup, "xml") | 速度快、唯一支持XML的解析器 | 需要安装C语言库 |
| html5lib	| BeautifulSoup(markup, "html5lib")	 | 最好的容错性、以浏览器的方式解析文档、生成HTML5格式的文档 | 速度慢、不依赖外部扩展 |

## 基本使用

```
html = """
<html>

    <head>
        <title>The Dormouse's story</title>
    </head>
    
    <body>
        <p class="title" name="dromouse">
            <b>The Dormouse's story</b>
        </p>
        <p class="story">
            Once upon a time there were three little sisters; and their names were
            <a href="http://example.com/elsie" class="sister" id="link1">
            <!-- Elsie -->
            </a>,
            <a href="http://example.com/lacie" class="sister" id="link2">
            Lacie
            </a> 
            and
            <a href="http://example.com/tillie" class="sister" id="link3"> 
            Tillie
            </a>;
            and they lived at the bottom of a well.
        </p>
        <p class="story">...</p>
"""

from bs4 import BeautifulSoup
soup = BeautifulSoup(html, 'lxml')

print(soup)   
# bs4.BeautifulSoup

print(soup.title)  
# 标签 bs4.element.Tag

print(soup.title.name) 
#标签的名称

#print(soup.p.attrs['name'])  
#标签的属性

print(soup.p.text)  
#标签的文字内容

print(soup.p.get_text()) 
#标签的文字内容

print(soup.head.title.string) 
#标签的文字内容 bs4.element.NavigableString

```

## 子节点和子孙节点
* .contents 返回一个列表，包含所有子节点（文字，标签，换行符，空格等）
* .children 返回子节点迭代对象（文字，标签，换行符，空格等），需要遍历输出
* .descendants 返回子孙节点的迭代对象（文字，标签，换行符，空格等），需要遍历输出
* enumerate() 枚举某个对象

```
print(soup.p.contents) 
#返回所有子节点（文字，标签，换行符，空格等）

print(soup.p.children) 
#list_iterator object

print(type(soup.p.children)) 
for  i,child in enumerate(soup.p.children):
    print(i,child)
 
 print(soup.p.descendants)
for i, child in enumerate(soup.p.descendants):
    print(i, child)
    
```


## 父节点和祖先节点
* .parent #返回父亲节点（文字，标签，换行符，空格等）
* .parents #返回所有祖先节点（文字，标签，换行符，空格等）,需要遍历输出

```
print(soup.a.parent)

print(soup.a.parents)
for i,parent in enumerate(soup.a.parents):
    print(i,parent)
```

## 兄弟节点

* .next_siblings 后面的所有兄弟节点（文字内容，子标签，换行符，空格等）
* .previous_siblings 前面的所有兄弟节点（文字内容，子标签，换行符，空格等）

```
print(soup.a.next_siblings)
for i,next in enumerate(soup.a.next_siblings):
    print(i,next)
print("\n")   

print(soup.a.previous_siblings)
for i,pre in enumerate(soup.a.previous_siblings):
    print(i,pre)
    
```

## 标签选择器
###### find_all(name,attrs,recursive,text,**kwargs)
###### find( name , attrs , recursive , text , **kwargs )
根据名称，属性，文字内容查找

```
html='''
<div class="panel">
    <div class="panel-heading">
        <h4>Hello</h4>
    </div>
    <div class="panel-body">
        <ul class="list" id="list-1">
            <li class="element">Foo</li>
            <li class="element">Bar</li>
            <li class="element">Jay</li>
        </ul>
        <ul class="list list-small" id="list-2">
            <li class="element">Foo</li>
            <li class="element">Bar</li>
        </ul>
    </div>
</div>
'''
```
###### 利用名称
```
from bs4 import BeautifulSoup
soup = BeautifulSoup(html, 'lxml')

print(soup.find_all('ul'))  
#bs4.element.ResultSet



print(soup.find_all('ul')[0])
 #bs4.element.Tag

for u in soup.find_all('ul'):
    print(u)
```

###### 利用属性  
```
print(soup.find_all(attrs={'id': 'list-1'}))   bs4.element.ResultSet

print(soup.find_all(id='list-1'))  #简写

print(soup.find_all('ul',class_='list'))

print(soup.find_all(class_='element'))

```

###### 利用文本
```
print(soup.find_all(text='Foo'))
```

######  find_parents()  
返回所有祖先节点
###### find_parent()
返回直接父节点

###### find_next_siblings()
返回后面所有兄弟节点  
###### find_next_sibling()
返回后面第一个兄弟节点

###### find_previous_siblings()
返回前面所有兄弟节点  
###### find_previous_sibling()
返回前面第一个兄弟节点

######  find_all_next()
返回节点后所有符合条件的节点  
###### find_next()
返回第一个符合条件的节点

######  find_all_previous()
返回节点后所有符合条件的节点 
###### find_previous()
返回第一个符合条件的节点


