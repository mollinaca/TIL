
# 環境

ubuntu 20.04 LTS

# 手動作業

`<>` で囲ったものはファイル名や固有の名前など。  
適宜読み替える。  

## sho ユーザの鍵配置

```
$ scp <PubKeyFile> sho@<IPaddr>:/home/sho/
$ ssh sho@<IPaddr>
$ mkdir .ssh
$ chmod 700 .ssh
$ mv <PubKeyFile> .ssh/
$ cat <PubKeyFile> >>authorized_keys
$ chmod 400 authorized_keys
$ logout
$ ssh -i <PrivateKeyFile> sho@<IPaddr> -> 鍵認証でログインできることを確認
```

## root ユーザの鍵配置

```
$ scp <PubKeyFile> sho@<IPaddr>:/home/sho/
$ ssh sho@<IPaddr>
$ sudo mv <PubKeyFile> /root/
$ sudo su -
# chown root:root <PubKeyFile>
# mkdir .ssh
# chmod 700 .ssh
# mv <PubKeyFile> .ssh/
# cat <PubKeyFile> >>authorized_keys
# chmod 400 authorized_keys
# logout
$ ssh -i <PrivateKeyFile> root@<IPaddr> -> 鍵認証でログインできることを確認
```

## static IP address 設定

※ root でログイン後
```
# cd /etc/netplan/
# mv 00-installer-config.yaml 00-installer-config.yaml.bak
# cp -pi 00-installer-config.yaml.bak 99_config.yaml
# vi 99_config_yaml
```
```
network:
  version: 2
  renderer: networkd
  ethernets:
    <I/F名>:
      dhcp4: false
      dhcp6: false
      addresses: [<IpAddr>/24]
      gateway4: <GatewayAddr>
      nameservers:
        addresses: [<NameServers>]
```
```99_config.yaml
# netplan apply -> IPアドレスが代わり、セッションが切断される
~~~
$ ssh -i .ssh/<PrivateKeyFile> root@<IPaddr> -> ログインできることを確認
# ip a -> <I/F> に指定したIPアドレスがせっていされていることを確認
```

上記までで、一般ユーザ/rootユーザでのsshkeyでのログインと固定IPアドレスの設定が完了  

## 設定

### visudo

```
# update-alternatives --config editor -> vim.basic を選択
```
```
visudo


```





# Ansibel

ToBeWritten...
