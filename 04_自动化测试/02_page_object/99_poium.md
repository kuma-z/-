# `poium`

> 一个page object模型的UI自动化框架
>
> selenium、appium均可使用
>
> `pip install poium`



## 特点

- Page页面书写
    - 继承`Page, NewPageElement`
    - selenium方法被封装，元素定位书写方式简单
    - 
- 元素定位
    - 添加描述，`describe="xxxx"`
    - 自动在控制台输出日志
    - 
- testcase书写
    - 同样书写简便
    - 文本框传值，`self.page.login_username = "zch"`
    - 按钮点击，`self.page.login_button.click()`
    - frame切换
        - `self.page.dialog_iframe.switch_to_frame()`
        - `self.page.switch_to_parent_frame() `
    - 翻页查找元素，`self.page.load_add_btn.move_to_element()`
    - 

## 举例

```python
from poium import Page, NewPageElement
from selenium import webdriver

class LDPLoginPage(Page):
    login_username = NewPageElement(id_='j_username')
    login_passwd = NewPageElement(id_='j_password')
    login_code = NewPageElement(id_='j_code')
    login_button = NewPageElement(id_='loginBtn')

class MainPage(Page):
    main_static_management = NewPageElement(xpath='//*[text()="静态数据管理"]')
    main_static_airline = NewPageElement(xpath='//*[text()="航空公司静态数据"]')
    
class AirStaticPage(Page):
    win_frame = NewPageElement(xpath='//*[@src="/flm//airlineStatic/frameMain" and @class="h-window"]')
    right_frame = NewPageElement(id_='frameRight')
    left_frame = NewPageElement(id_='frameLeft')
    create_airline = NewPageElement(id_='createAirlineBtn')
    dialog_iframe = NewPageElement(css='.tui-dialog-iframe')
    add_airline_edit = NewPageElement(id_='addAirlineEdit')
    save_btn = NewPageElement(id_='saveBtn')
    load_add_btn = NewPageElement(id_='loadAddBtn')
    create_air_succ = NewPageElement(css='.tui-dialog-btn-panel .button')
```



```python
from ldp_page import LDPLoginPage, MainPage, AirStaticPage
import time

class TestLdp(object):
    def setup(self):
        self.driver = webdriver.Chrome()
        self.url = "http://10.221.159.168:8081/flm/index.jsp"

    def test_ldp(self):
        self.page = LDPLoginPage(driver)
        self.page.get(self.url)

        # 用户登录
        self.page.login_username = "zch"
        self.page.login_passwd = "LDP2014test"
        self.page.login_code = "1234"
        self.page.login_button.click()

        # 打开进入的欢迎页
        time.sleep(1)
        self.page = MainPage(driver)
        self.page.main_static_management.click()
        self.page.main_static_airline.click()

        # 点击进入飞机静态数据页面
        self.page = AirStaticPage(driver)
        self.page.win_frame.switch_to_frame()
        self.page.right_frame.switch_to_frame()
        self.page.create_airline.click()

        # 创建飞机形态数据
        self.page.switch_to_parent_frame()       # 回到父frame，注意用法
        self.page.dialog_iframe.switch_to_frame()
        self.page.add_airline_edit="SS"
        self.page.save_btn.click()
        self.page.switch_to_parent_frame()
        self.page.create_air_succ.click()

        # 默认打开页面输入页面内容
        self.page.right_frame.switch_to_frame()
        self.page.load_add_btn.move_to_element() # 自动翻页查找
        self.page.load_add_btn.click()

    def teardown(self):
        time.sleep(10)
        self.driver.quit()
```

