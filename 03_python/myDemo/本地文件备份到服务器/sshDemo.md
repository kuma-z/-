```python
# sshDemo.py
# 链接ssh
# author: z

import paramiko

def ssh_conn(ip, user, password, port=22):
    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    # 建立连接
    try:
        ssh.connect(ip,port,user,password,timeout = 10)
        #输入linux命令
    except:
        print('ssh connect error...')
    return ssh

def ssh_cmd(ssh, cmd):
    stdin,stdout,stderr = ssh.exec_command(cmd)
    # 输出命令执行结果
    result = stdout.read().decode()
    print(result)

if __name__ == "__main__":
    # 服务器相关信息,下面输入你个人的用户名、密码、ip等信息
    ip = "118.89.198.152"  
    port =  22
    user = "root"
    password = "GAImima@yun!0213"
    ssh=ssh_conn(ip,user,password)
    cmd = 'ls /etc | grep -E "^t"'
    ssh_cmd(ssh, cmd)
    ssh.close()
```

