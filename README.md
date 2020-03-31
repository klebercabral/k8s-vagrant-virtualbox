# Projeto Virtualbox K8S

3 VM's com duas placas de rede:
 - uma nat (saída internet)

 - uma hostonly (rede privada 192.168.33.*)

Vagrantbox: bento/ubuntu-18.04

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

## Criar VM's no Virtualbox e configuar K8S via Ansible:

```zsh
vagrant up
```

## Roles fork from

https://github.com/iaasweek/ansible

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)