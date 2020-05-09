## 如何从命令行创建一个az集群

```
创建一个新的资源组，名字为 ata-op
az group create --name ata-op --location southeastasia

创建创建虚拟网络(vnet,名称为 opvnet)和子网(subnet,名称为 opsubnet)。
子网为 10.0.0.0/24。也就是说我们可以使用 10.0.0.0 到 10.0.0.255 的 ip
az network vnet create -g ata-op -n opvnet --address-prefix 10.0.0.0/24
az network vnet subnet create -g ata-op --vnet-name opvnet -n opsubnet --address-prefix 10.0.0.0/24
检查一下虚拟网络和子网有没有建好 az network vnet subnet list -g ata-op --vnet-name opvnet

可以开几个公网 ip，其中--allocation-method Static 表示启用固定的公网 ip 。当然其实你只需要一个公网 ip 就够了。
az network public-ip create -g ata-op -n ata-op-ip1 --allocation-method Static
az network public-ip create -g ata-op -n ata-op-ip2 --allocation-method Static
az network public-ip create -g ata-op -n ata-op-ip3 --allocation-method Static

下一步创建三张网卡(nic)，并且给网卡都配上公网 ip 和内部 ip。
az network nic create -g ata-op --vnet-name opvnet -n ata-op1-nic --subnet opsubnet --private-ip-address 10.0.0.10
查看一下这张网卡的 ip-config(可以看到，现在只有一个 ip-config，名为 ipconfig1)
az network nic ip-config list -g ata-op --nic-name ata-op1-nic
给这张网卡加上 public ip
az network nic ip-config update -g ata-op -n ipconfig1 --nic-name ata-op1-nic --public-ip-address ata-op-ip1
也可以在创建的时候直接指定 public-ip
az network nic create -g ata-op --vnet-name opvnet -n ata-op2-nic --subnet opsubnet --private-ip-address 10.0.0.20 --public-ip-address ata-op-ip2
az network nic create -g ata-op --vnet-name opvnet -n ata-op3-nic --subnet opsubnet --private-ip-address 10.0.0.30 --public-ip-address ata-op-ip3

最后创建三台虚拟机，使用centos,绑定前面配好的网卡，设置好用户，并提供公钥（用于ssh登录）
az vm create -g ata-op -n ata-op1 --image CentOS --nics ata-op1-nic --admin-username azure --ssh-key-value ~/.ssh/ata.pub
az vm create -g ata-op -n ata-op2 --image CentOS --nics ata-op2-nic --admin-username azure --ssh-key-value ~/.ssh/ata.pub
az vm create -g ata-op -n ata-op3 --image CentOS --nics ata-op3-nic --admin-username azure --ssh-key-value ~/.ssh/ata.pub
```
