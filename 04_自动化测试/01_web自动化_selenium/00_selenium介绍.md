# selenium

> https://www.selenium.dev/



## 核心组件

- selenium webdirver client
- selenium dirivers
- selenium1（ selenium-rc）
    - selenium3.0开始不支持该组件
- selenium IDE
    - 基本不用
    - katalon automation recorder比selenium IDE更高级
- selenium grid



## 和appium

|         APPIUM |      | SELENIUM        |
| -------------: | :--: | :-------------- |
|         appium |  ==  | selenium server |
|   ChromeDriver |  ==  | ChromeDriver    |
|  Appium Client |  ==  | Selenium Client |
|  Selenium Grid |  ==  | Selenium Grid   |
| Appium Desktop |  ==  | Selenium IDE    |



### python selenium文档

https:///selenium-python.readthedocs.io/





### 本质操作流程

selenium.py 将你的操作封装成请求发送给chromedriver

由chromedriver执行操纵