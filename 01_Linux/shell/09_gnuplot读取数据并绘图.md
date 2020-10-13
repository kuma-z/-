```shell
echo '1
3
5
7
3
4
1
2
6
8
9'  | gnuplot -e "set terminal dumb;plot '<cat' using 1 with line"
```
![](.\image\gnuplot.png)


```shell
awk '{print $1}' /tmp/nginx.log | 
sort | uniq -c | sort -nr | head -20 
|gnuplot -e "set term dumb;plot 
'<cat' u 1:(column(0)):ytic(2) w l"
```