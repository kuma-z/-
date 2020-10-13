# Page Object

> PO来源：https://martinfowler.com/bliki/PageObject.html
>
> selenium python官方：**https://selenium-python.readthedocs.io/page-objects.html**
>
> Firefox开源PyPOM：https://github.com/mozilla/PyPOM/

- driver的封装
    - 完成对web/android/ios/接口驱动的封装
- page的封装
    - 完成对各种页面的封装
- testcase
    - 调用page对象实现业务并断言
- 数据封装
    - 配置文件和数据驱动
- Utils
    - 其他功能封装，改进原生框架不足
- 



***如果你的测试方法中有WebDriver APIs，那你的PO就写错了。***



---

## 开发目标

- 易于使用
- 结构清晰
    - PageObject对于页面对象
    - PageModules对于页面内容

- 只写测试，不写基础
- 尽量防止样板代码
- 不需要自己管理浏览器
- 运行时选择浏览器，而不是类级别定义
- 不需要直接接触selenium



## PO原则

- 用公共方法代表UI所提供的功能
- 不要暴露页面内部元素给外部
- 方法应该返回其他的PageObject或者返回其他用于断言的数据
- 同样的行为不同的结果可以建模为不同的方法
- 不要再方法内加断言
- 不需要建模UI内的所有元素



## 变化

- 定位符发生变化，需要支持多平台
- 操作流程可能变化
- 多平台
- 变量化
- 



### yaml

![](.\image\yaml解析.png)



### 抽象原则

- 抽离变化部分
    - 安卓/ios，页面一致，使用同一数据文件维护
    - 小程序、h5、web差别很大，使用各自数据文件维护
- 