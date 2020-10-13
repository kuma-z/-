# charles



## 一些基础概念



### fake stub mock

- fake：替代真实环境，有简化的逻辑
- stub：纯预定义数据，不能动态变更
- mock：可自定义返回
    - map remote，切换线上环境与备份环境，或内部搭建测试环境，fake模式
        - 不同请求 -> 不同的结果
    - map local，把线上的请求变成本地文件请求，stub模式
        - 不同请求 -> 相同的结果
    - reverse proxy，把线上请求转发，proxy模式
- proxy：挡板，可在原结果基础上进行修改
- spy：监听特定方法的调用