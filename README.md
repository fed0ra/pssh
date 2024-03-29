远程执行命令、拷贝本机目录或文件到远程主机、拷贝远程主机目录或文件到本机

## 前提

目标主机安装rsync


## 1. 修改ip.txt文件，格式如下 

    cat ip.txt
    192.168.133.151:22
    192.168.133.152:22

## 2. 远程执行命令

    # 在某一台远程主机执行
    ./pssh.sh ssh 192.168.133.151 off 'ip r'
    # 批量执行
    ./pssh.sh ssh ip.txt off 'ip r'

## 3. 拷贝本机目录或文件到远程主机

    # 拷贝文件到远程主机
    ./pssh.sh rsync ip.txt off /root/batch-sshkey.sh /root/

    # 拷贝目录到远程主机，目录后加/会拷贝目录下文件，不加/会拷贝目录
    ./pssh.sh rsync ip.txt off /root/testdir /root/ 

## 4. 拷贝远程主机目录或文件到本机

    # 拷贝远程主机文件到本机，本机会创建一个以远程主机ip命名的目录
    ./pssh.sh hss 192.168.133.152 off /root /root/1.txt

    # 拷贝远程主机目录到本机，目录后加/会拷贝目录下文件，不加/会拷贝目录
    ./pssh.sh hss 192.168.133.152 off /root /root/testdir
