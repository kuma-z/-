```python
from getfileDetails import get_file_list

def get_backup_list(backup_file, back_res):
    with open(backup_file, mode='r', encoding='utf-8') as f:
        ls = f.readlines()
    for l in ls:
        back_res.append(l[:-1])
    return back_res

def get_add_list(cmd, path, res, backup_file):
    new_res = get_file_list(cmd, path, [])
    back_res = get_backup_list(backup_file, [])
    return list(set(new_res)-set(back_res))

if __name__ == "__main__":
    path = r" G:\自己的库"
    cmd = "dir"
    res = []
    filename = r'G:\自己的库\backup.log'
    #output_backuplog(filename)
    res = get_add_list(cmd, path, [], filename)
    print(res)
```

