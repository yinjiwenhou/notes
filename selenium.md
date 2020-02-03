# selenium

## 选择元素
### 选择元素基本方法
* find_element_by_id
* find_elements_by_class_name
* find_elements_by_tag_name
### css选择器
**css 选择语法**

### XPath选择器
**XPath 选择语法**

## 操作元素
### 操控元素基本方法
* 获取元素的文本内容
```python
element.text
```

* 点击按钮
```python
element.click()
```
* 获取元素属性
```python
element.get_attribute('class')
element.get_attribute('outerHTML') #获取整个元素对应的HTML
element.get_attribute('innerHTML') #获取某个元素内部的HTML文本内容
```
