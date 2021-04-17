## Se maquina for clonada Ubuntu ou Centos/AlmaLinux
```sh
sudo rm /etc/machine-id
sudo systemd-machine-id-setup
reboot
```

## Criando certificado admin1x
```sh
## Usuario admin1x UBUNTU
ssh lc@192.168.3.71
sudo adduser admin1x
sudo passwd admin1x
su - admin1x
sudo usermod -a -G adm,sudo,cdrom,dip,plugdev,lxd admin1x


admin1x@ansibleserver:~$ ansible --version
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/admin1x/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.8.5 (default, Jan 27 2021, 15:41:15) [GCC 9.3.0]


# Executar uma unica vez
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_admin1x -C "admin1x.home-network.io"
ssh-copy-id -i /home/admin1x/.ssh/id_ed25519_admin1x.pub admin1x@192.168.3.71

# teste para ver se esta ok
ssh -i /home/admin1x/.ssh/id_ed25519_admin1x admin1x@192.168.3.71

#sudo 
echo "admin1x ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/admin1x


##### AlmaLinux
## Usuario admin1x Almalinux
ssh lc@192.168.3.72
su -
adduser admin1x
passwd admin1x
su - admin1x
echo "admin1x ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/admin1x

# teste se esta funcionaod
sudo -i #nao pode pedir senha.

#disable selinux
vi /etc/selinux/config 
de: SELINUX=enforcing
para: SELINUX=disabled

#disable firewall
systemctl disable firewalld

#reboot
reboot

# adicionado a chave:
ssh -i id_ed25519_admin1x admin1x@192.168.3.71
ssh-copy-id -i /home/admin1x/.ssh/id_ed25519_admin1x.pub admin1x@192.168.3.72
```

## How to Restart Network Service on CentOS 8 or RHEL 8
```
sudo systemctl start NetworkManager.service 
sudo systemctl stop NetworkManager. service.
sudo systemctl restart NetworkManager.service.
sudo nmcli networking off sudo nmcli networking on.
```

## Criando diretorio do projeto
```sh
sudo mkdir -p /projeto/ansible/key
sudo chown admin1x:admin1x /projeto -R
cp ~/.ssh/id_ed25519_admin1x* /projeto/ansible/key/

```


Configurando o git para repistorio:
```sh 
git config --local user.email "xxx"
git config --local user.name "xx"
git remote add origin git@github-admin1x:luperciniocosta/ansible.git




#lupercinio.costa@gmail.com
#https://github.com/luperciniocosta/ansible

```

