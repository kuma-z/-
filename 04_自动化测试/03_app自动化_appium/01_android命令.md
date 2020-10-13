# Android命令

- `adb logcat`，操作日志显示

    - ```shell
        07-13 17:22:42.132  1582 10724 W XSpaceManagerService: checkXSpaceControl, from:com.miui.home, to:com.tencent.mm, with act:android.intent.action.MAIN, callingUserId:0, toUserId:0
        07-13 17:22:42.133  1582 10724 I ActivityManager: START u0 {act=android.intent.action.MAIN cat=[android.intent.category.LAUNCHER] flg=0x10200000 cmp=com.tencent.mm/.ui.LauncherUI bnds=[704,1533][872,1701] (has extras)} from uid 10022
        07-13 17:22:42.163  4046  4431 I ProcessMonitor: onForegroundInfoChanged: ForegroundInfo{mForegroundPackageName='com.tencent.mm', mForegroundUid=10147, mForegroundPid=32461, mLastForegroundPackageName='com.miui.home', mLastForegroundUid=10022, mLastForegroundPid=29590, mMultiWindowForegroundPackageName='null', mMultiWindowForegroundUid=-1, mFlags=0}
        07-13 17:22:42.163  4046  4431 I GameBoosterService: onForegroundInfoChanged: Cur=com.tencent.mm         last=com.miui.home
        07-13 17:22:42.165  4046  4125 I GuardService: notifyChange! preName = ComponentInfo{com.miui.home/com.miui.home.launcher.Launcher}; curName = ComponentInfo{com.tencent.mm/com.tencent.mm.ui.LauncherUI}
        07-13 17:22:42.176  4046  4431 D GameBoosterService: onGameStatusChange foreground:ForegroundInfo{mForegroundPackageName='com.tencent.mm', mForegroundUid=10147, mForegroundPid=32461, mLastForegroundPackageName='com.miui.home', mLastForegroundUid=10022, mLastForegroundPid=29590, mMultiWindowForegroundPackageName='null', mMultiWindowForegroundUid=-1, mFlags=0}
        07-13 17:22:42.187  3180  3180 D TouchAssistant: getPackageNameFromPid packageName:com.tencent.mm
        07-13 17:22:42.187  3180  3180 D TouchAssistant: onTopAppChanged packageName:com.tencent.mm
        07-13 17:22:42.259 32461 32471 I com.tencent.mm: CollectorTransition concurrent copying GC freed 248430(11MB) AllocSpace objects, 55(1472KB) LOS objects, 37% free, 40MB/64MB, paused 254us total 354.931ms
        07-13 17:22:42.559  1582  1736 I Timeline: Timeline: Activity_windows_visible id: ActivityRecord{7a315c0 u0 com.tencent.mm/.ui.LauncherUI t15648} time:1449395315
        07-13 17:22:42.618  3180  3180 D TouchAssistant: topActivity.getPackageName(),packageName:com.tencent.mm
        07-13 17:22:42.618  3180  3180 D TouchAssistant: onTopAppChanged packageName:com.tencent.mm
        ```

    - `cmp=com.tencent.mm/.ui.LauncherUI`

- `adb shell am start -W -S -n com.tencent.mm/.ui.LauncherUI`

    - `-W`，等待完全启动

    - `-S`，杀掉当前进程

    - `-n`，

    - ```shell
        am start -W -S -n com.tencent.mm/.ui.LauncherUI
        Stopping: com.tencent.mm
        Starting: Intent { cmp=com.tencent.mm/.ui.LauncherUI }
        Status: ok
        Activity: com.tencent.mm/.ui.LauncherUI
        ThisTime: 655
        TotalTime: 655
        WaitTime: 680
        Complete
        ```

    - 

- 获得app入口

    - locat
    - 方法
        - 结束app进程
        - `adb logcat | grep -i display`
    - `adb shell dumpsys activity activities top`
    - `adb shell apkanalyse`

- 1

- 





## appium配置

![](.\image\appium设置.png)

录制脚本

![](.\image\appium录制脚本.png)

appiun官方示例代码

https://github.com/appium/appium/blob/master/sample-code/python



界面元素定位

- 工具
    - appium desktop
    - uiautomatorviewer（推荐）
        - 不能与appium同时使用
- 策略
    - id（resource-id）
    - accessibility id（content-desc）
    - xpath全能支持
- 





### 自定义控件识别

- 基本定位
- 父控件定位+百分比定位
- 图像识别
- OCR，图形文字识别