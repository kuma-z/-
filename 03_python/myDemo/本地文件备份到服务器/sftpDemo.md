```python
# coding: UTF-8
import paramiko
from sshDemo import ssh_conn, ssh_cmd

def trans_conn(ip, user, password, port=22):

    try:
        transport = paramiko.Transport((ip, port))
        transport.connect(username=user, password=password)
        sftp = paramiko.SFTPClient.from_transport(transport)
    except:
        print("connect to sftp error...")
    return sftp

def put_files(sftp, ssh, filename):
    ssh_cmd(ssh, 'mkdir -p ' + '/home/z/'+('/').join(filename.split('\\')[1:-1])+'/')
    # 将location.txt 上传至服务器 /tmp/f_win.txt
    sftp.put(filename, '/home/z/'+('/').join(filename.split('\\')[1:]))

if __name__ == "__main__":
    ip = "118.89.198.152"  
    port =  22
    user = "root"
    password = "GAImima@yun!0213"
    filename = r'G:\自己的库\测试开发\03_python\myDemo\ssh\00_需求.md'
    ssh=ssh_conn(ip,user,password)
    sftp = trans_conn(ip, user, password)
    put_files(sftp, ssh, filename)
    ssh.close()
    sftp.close()
```

