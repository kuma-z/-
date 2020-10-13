```python
# allback.py
# 全量备份文件并生成backup日志
# author: z

from getfileDetails import get_file_list, output_backup
from sshDemo import ssh_conn, ssh_cmd
from sftpDemo import trans_conn, put_files

path = r" G:\自己的库"
cmd = "dir"
res = []
filename = r'G:\自己的库\backup.log'
ip = "118.89.198.152"  
port =  22
user = "root"
password = "GAImima@yun!0213"

output_backuplog(filename)
files = get_file_list(cmd, path, res)
ssh = ssh_conn(ip,user,password)
sftp = trans_conn(ip, user, password)

for file in files:
    put_files(sftp, ssh, file)
```

