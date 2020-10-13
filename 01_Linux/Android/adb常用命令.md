# adb

## adb命令

- `adb devices`，获取连接设备列表
- `adb get-state`，获取设备状态
    - device，设备正常连接
    - offline，连接出现异常，设备无响应
    - unknown，没有连接设备
- `adb logcat`，打印日志
- `adb -s device-id`，使用特定设备
- `adb start-server`/`adb stop-server`
- `adb install xxx.apk`/`adb install -r xxx.apk`，-r表示覆盖，保留缓存和数据
- `adb uninstall package`/`adb uninstall -k package`，-k表示卸载时，保留缓存和数据
- `adb shell pm list packages`，查看所有应用包名
    - `adb shell pm list package -s `，列出系统应用
    - `adb shell pm list package -3`，列出第三方应用
    - `adb shell pm list package -f`，列出应用包名、对应apk名及存放位置
- `adb shell service list`，查看服务
- `adb shell am start -n your.package.name/your.package.name-activity`，启动app
- `adb shell ps`
- `adb shell kill pid`
- `adb shell ps -x pid`
- `adb shell cat /proc/meminfo`，查看系统当前内存使用情况
- `adb shell umpsys meminfo package`，查看指定包名的内存使用情况
- 



