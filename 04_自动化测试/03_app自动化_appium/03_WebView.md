#  WebView

## 多种架构

![](.\image\WebView多种架构.png)

## WebView组件实现

> 会在组件中发现`android.webkit.WebView`





## WebView测试

### 模拟器的测试

- webview控件会被映射为原生控件，类型位View，其中的文本内容会变成content-desc或者text
    - 6.0，content-desc属性的View控件
    - 9.0，text属性的View控件
- 可以使用`fing_element_by_accessibility_id`进行定位
- 



### 真机测试

- 如果app没有开启webview的调试属性，是无法分析内部的控件的
    - 个别手机会默认打开此属性
    - 未打开，需研发配合帮忙打开
- 



## WebView 原理（微信小程序同样需要运用此原理）

- 获取webview进程
    - `adb shell cat /proc/net/unix | grep -i webview`
    - 开启webview的app会开启一个domain socket方便调试
- 映射domain socket为本地socket
    - `adb forward tcp:$port localabstract:webview_devtools_remote_$pid`
    - `adb forward --list`，查看映射的端口，注意多机并存的情况
    - 获取对应的webview组件版本
        - chrome 远程调试协议
            - http://localhost:$port/json/version
            - http://localhost:$port/json/list
    - 
- 查看调试入口
    - `curl http://127.0.0.1:$port/json/version`
    - chrome浏览器输入`chrome://inspect/#devices`
        - 当app打开webview页面时，可以通过这里进入
        - chrome版本高于62时，可能有坑
    - 
- devtools
    - https://chromedevtools.github.io/devtools-protocol/
- 



### WebView测试用例

- 不需要css定位：直接使用accessibility-id或者xpath就可以直接定位到的
- 需要css定位以及其他的js执行能能：context api 



###  context

- 获取当前context
    - `driver.contexts`
    - `driver.current_context`
- context切换
    - `driver.swtich_to.context(driver.contexts[1])`
- ChromeDriver
    - 使用webview时，需要加载对应版本的webdriver
    - `caps['chromedriverExecutableDir'] = "xxxxx"`
- handles窗口
    - 获取当前
        - `driver.window_handles`
    - 切换窗口
        - `driver.switch_to.window(driver.window_handles[1])`
    - 
- `find_view_by_xxx`
    - 在webview中和在app原生框架下，相同的方法名可能代表含义不同
- 

