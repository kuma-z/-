## Monkey

> 安卓的压测工具
>
> http://developer.android.com/studio/test/monkey



## 主要适用范围

- 健壮性测试
    - `adb shell monkey -p com.xueqiu.android --throttle 1000 --pct-touch 50 --pct-motion 50 -v 500`
        - `-p ......  500`，500个事件
        - `--throttle 1000`，每次事件间隔1000ms
        - `--pct-xxx 50`，xxx事件占比50%
- 





## 异常log

- /data/anr/traces.txt\
- `adb logcat -s *:E`，异常
- `adb logcat -s *:W`，警报
- 崩溃实验
    - demo app
        - github cloudgrey TheApp-v1.8.1.apk
    - gps未授权情况下会崩溃
- 



## Maxim

- github  zhangzhao4444  maxim
- 使用方法
    - ![](.\image\maxim.png)
- 





## AppCrawler

- github  seveniruby appcrawler