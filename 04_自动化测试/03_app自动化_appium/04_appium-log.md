# appium-log

## appium -g

- `appium -g xxx.log`
    - 将所有的输出打印到xxx.log
    - log大致内容划分
        - adb devices
        - 判断待测系统
        - 安装settings apk unclock
        - 推送uiautomator到手机并启动
        - 启动app
        - http请求，element  elements  click  value
    - log内容中操作，基本都是通过adb命令实现
- 