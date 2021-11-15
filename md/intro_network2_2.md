# ネットワークハンズオン

[スライド資料](../pdf/intro_network2_2.pdf)
<br> 
<br> 

## 概要
- プロトコルの説明（HTTP, TCP, UDP, IP, Ethernet）
- Wireshark
- ソケットプログラミング
<br> 
<br> 

## ハンズオン内容
---
## プロトコルの説明
HTTP，TCP，UDP，IP，Ethernetについて簡単に説明した．TCP/IPの階層モデルの各階層に対応する，プロトコルに触れ，パケットの中身をイメージをつかむ
#### 参考サイト
- 階層のお話（https://www.infraexpert.com/study/tcpip.html）
- HTTPのお話（https://www.infraexpert.com/study/tcpip16.html）
- TCPのお話（https://www.infraexpert.com/study/tcpip8.html）
- UDPのお話（https://www.infraexpert.com/study/tcpip12.html）
- IPのお話（https://www.infraexpert.com/study/tcpip1.html）
- Ethernetのお話（https://www.infraexpert.com/study/ethernet.html）
<br>
<br>

## Wireshark
パケット解析などに利用されるWiresharkについて触れた．使い方になれるため，CTF問題のネットワーク問題に取り組んだ．<br>
- Wireshark（https://www.wireshark.org/download.html）<br>
- 演習で利用した問題（https://www.slideshare.net/ctf4b/ctf-for-60147258）
<br>
<br>

## ソケットプログラミング
ソケットプログラミングでは，プログラミングでネットワークの通信を行う方法を学ぶ．

- サーバー側のプログラム
```python
import socket

host = "0.0.0.0"
port = 60000

serversock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
serversock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
serversock.bind((host, port)) 
serversock.listen(10)

while True:
    clientsock, client_address = serversock.accept()
    rcvmsg = clientsock.recv(1024)
    if len(rcvmsg) == 0:
        continue
    else:
        print('{}:{} -> {}'.format(host,
                                   client_address[1], rcvmsg.decode('utf-8')))
                                   
    #clientsock.sendall(rcvmsg)
clientsock.close()
```
- クライアント側のプログラム

```python
import socket

host = "192.168.7.138"
port = 60000

client =socket.socket(socket.AF_INET , socket.SOCK_STREAM) 

client.connect((host,port))

print("何か文字を入力してください")
input_string = input()
client.send(input_string.encode('utf-8'))
#respnse = client.recv(4096)
#print(respnse.decode('utf-8'))
```