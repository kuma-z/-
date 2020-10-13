```python
# getfileDetail.py
# 获取某一目录下所有非目录的文件路径信息
# author: z

import subprocess

def get_file_list(cmd, path, res):
    (status, uploadRes) = subprocess.getstatusoutput(cmd+path)

    if status != 0:
        print(f"get {cmd} {path} detail error...")
        exit

    ls = uploadRes.split("\n")[7:-2]
    
    if not ls:
        # 当文件夹下没有文件时，返回
        return res
    
    for i in range(len(ls)):
        if "DIR" not in ls[i]:
            res.append(path[1:]+'\\'+ls[i].split(' ')[-1])
        else:
            # 当文件类型是文件夹的时候，递归查询该文件夹
            #print(path+'\\'+ls[i].split(' ')[-1])
            get_file_list(cmd, path+'\\'+ls[i].split(' ')[-1], res)
            
    return res

def output_backuplog(filename):
    rs = get_file_list(cmd, path, res)
    with open(filename, 'w') as f:
        for r in rs:
            f.write(r+'\n')
            
if __name__ == "__main__":
    path = r" G:\自己的库"
    cmd = "dir"
    res = []
    filename = r'G:\自己的库\backup.log'
    output_backuplog(filename)

```

