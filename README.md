# Projeto Virtualbox K8S

3 VM's com duas placas de rede:
 - uma nat (saída internet)

 - uma hostonly (rede privada 192.168.33.*)

Vagrantbox: ubuntu/bionic64

Master

Processador: 2 vCPU

Memória: 2GB de RAM

Workers

Processador: 1 vCPU

Memória: 1GB de RAM

## Requisitos

- ansible

- vagrant

- virtualbox

## Criar RSA Key:

```zsh
ssh-keygen -q -N '' -f ./id_rsa
```

## Criar VM's no Virtualbox:

```zsh
vagrant up
```

## Criar arquivo de inventário (hosts) com conteúdo:

```zsh
vim hosts
```

```vim
[k8s_master]
master ansible_host=192.168.33.10

[k8s_workers]
node01 ansible_host=192.168.33.20
node02 ansible_host=192.168.33.30

[all:vars]
ansible_user=vagrant
ansible_ssh_private_key_file=./id_rsa
ansible_ssh_extra_args='-o StrictHostKeyChecking=no'
K8S_MASTER_NODE_IP=192.168.33.10
K8S_API_SECURE_PORT=6443
```

## Testar conectividade SSH:

```zsh
ansible all -i hosts -m ping
```

## Iniciar Cluster K8S e configurar Workers:

```zsh
ansible-playbook -i hosts main.yml
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)