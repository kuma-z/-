# 基础



```python
from selenium import webdriver

class TestXXXX(object):
    def setup(self):
        self.driver = webdriver.Chrome()
        self.driver.implicitly_wait(10)
        self.driver.get(url)
    
    def test_xxx(self):
        self.driver.find_element_by_xxxx
```

## 浏览器驱动

- chrome
    - https://npm.taobao.org/mirrors/chromedriver

## 定位符

- `find_element_by_partial_link_text()`
    - 根据部分链接文本

- `find_element_by_xpath()`
    - chrome技巧
    - https://www.w3schools.com/xml/xpath_syntax.asp
    - https://www.w3school.com.cn/xpath/xpath_syntax.ASP
- xpath定位在appium应用较多
  
- `find_element_by_css_selector()`
    - www.w3schools.com/cssref/css_selectors.asp
    - https://www.w3school.com.cn/cssref/css_selectors.asp
    - css在web应用较多



![](.\image\元素定位.png)

### chrome定位技巧 

> 在console下执行两个特别的函数

- `$x('xpath表达式')`
- `$('css表达式')`



## 基础操作

- `maximize_windown()`
- `fullscreen_window()`
- `quit()`
- `forward`
- `cookie`
    - `driver.get_cookies()`
    - `driver.add_cookie()`
    - ![](.\image\cookie.png)
- `switch`
- `execute_script`
    - 传入一段js代码，在浏览器中执行并返回结果
    - 可用于统计执行时间，性能
    - 这个结果比requests更加详细，且可以获取requests无法的到的一些内部指标

![](.\image\execute_script.png)

- `execute()`
    - 用于尚未继承到selenium的心的命令/操作方式的使用

- `webdriver.Remote()`
    - 调用远程服务器执行脚本
    - https://selenium-python.readthedocs.io/getting-started.html#using-selenium-with-remote-webdriver
    - 工作中更建议使用Remote模式

![](.\image\remote.png)



## 加载流程

- webdriver模式
    - python testcase -> chromedriver -> chrome
- remote模式
    - python testcase -> remote selenium server -> chromedriver -> chrome

- grid模式
    - python testcase -> grid hub（类似STF) -> grid node == selenium server -> chromedriver -> chrome





## ActionChains

`from selenium.webdriver.common.action_chains import ActionChains`

- `click(on_element=None)` ——单击鼠标左键
- `click_and_hold(on_element=None)` ——点击鼠标左键，不松开
- `context_click(on_element=None)` ——点击鼠标右键
- `double_click(on_element=None)` ——双击鼠标左键
- `drag_and_drop(source, target)` ——拖拽到某个元素然后松开
- `drag_and_drop_by_offset(source, xoffset, yoffset)` ——拖拽到某个坐标然后松开
- `key_down(value, element=None)` ——按下某个键盘上的键
- `key_up(value, element=None)` ——松开某个键
- `move_by_offset(xoffset, yoffset)` ——鼠标从当前位置移动到某个坐标
- `move_to_element(to_element)` ——鼠标移动到某个元素
- `move_to_element_with_offset(to_element, xoffset, yoffset)` ——移动到距某个元素（左上角坐标）多少距离的位置
- `perform()` ——执行链中的所有动作
- `release(on_element=None)` ——在某个元素位置松开鼠标左键
- `send_keys(*keys_to_send)` ——发送某个键到当前焦点的元素
- `send_keys_to_element(element, *keys_to_send)` ——发送某个键到指定元素