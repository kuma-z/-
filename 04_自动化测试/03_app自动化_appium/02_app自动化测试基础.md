## 大体流程

1、获取app入口

2、设置启动app配置

3、录制代码

隐式等待

​	`driver.implicitly_wait(10)`

4、appium desktop，只是用于入门，一般使用appium server

appium server安装

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install -g appium@1.11

-g表示全局安装
使用appium启动
如果不加-g表示安装当前目录，利于多版本共存
./node_modules/appium/build/lib/main.js启动
```





## 脚本流程

> 三要素：定位、交互、断言

- 导入依赖
    - python-client
        - https://github.com/appium/python-client
- 写配置
    - capabilities设置
- 初始化driver实例
- 调用api，写case
- 断言
- 退出



### capabilities设置

- app apk地址
- appPackage包名
- appActiviey activity名字
- automationName，默认使用uiautomator
- noReset fullReset，是否再测试前后充值环境
- unicodeKeyBoard resetKeyBoard是否需要输入非英文之外的语言并再测试完成后重置输入法





### api

#### 定位

- accessbility id。对应content-desc
- id，对应resource-id
- xpath
    - 使用相对定位，代码利于维护



#### 等待

- 隐式等待

    - 全局隐式等待

        - ```python
            driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS)
            # 默认0s，不等待
            ```

        - 

    - 

- 显示等待

    - ```java
        WebDriverWait wait = new WebDriverWait(driver, 10)
        WebElement element = wait.until(ExceptedConditions.elementToBeClickable(By.id("xxx")))
        ```

    - 

- 



#### TouchAciton

- 滚动操作

    - `swipe()`旧

        - `driver.swipe(1000,1000,200,200)`

    - `TouchAction`新

        - ```python
            action = TouchAction(driver)
            action.press(x=1000, y=1000).move_to(x=200, y=200).release().perform()
            ```

        - 进阶，根据屏幕百分比模拟操作

            - ```python
                rect = driver.get_window_rect()
                # 获取屏幕尺寸
                action = TouchAction(driver)
                action.press(x=rect['weight']*0.8, y=rect['height']*0.8).move_to(x=rect['weight']*0.2, y=rect['height']*0.2).release().perform()
                ```

            - 

        - 

    - 回退

        - `driver.back()`

- 



#### 截图

- `driver.get_screenshot_as_xxx`





## 页面广告弹框

- 使用黑名单
- 找到页面顶层元素点击（一般来说广告都在页面顶层）

![](.\image\广告处理.png)