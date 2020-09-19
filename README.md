# Lab de tests ansible

Collection d'images docker pour tester ses playbook Ansible.

[Voir le tuto sur le blog](https://www.sysadminascode.com/ansible-labs-et-tests/)

## Tags des images

### Master
Image master sur la quelle est installée Ansible.
- [acoilier/ubuntu-ansible:20.04 (Focal)](https://hub.docker.com/r/acoilier/ubuntu-ansible)

### Ubuntu
images server accessible en ssh
- [acoilier/ubuntu-sshd:20.04 (Focal)](https://hub.docker.com/r/acoilier/ubuntu-sshd)
- [acoilier/ubuntu-sshd:18.04 (Bionic)](https://hub.docker.com/r/acoilier/ubuntu-sshd)
- [acoilier/ubuntu-sshd:16.04 (Xenial)](https://hub.docker.com/r/acoilier/ubuntu-sshd)

### Débian
images server accessible en ssh
- [acoilier/debian-sshd:10 (Buster)](https://hub.docker.com/r/acoilier/debian-sshd)
- [acoilier/debian-sshd:9 (Stretch)](https://hub.docker.com/r/acoilier/debian-sshd)
- [acoilier/debian-sshd:8 (Jessie)](https://hub.docker.com/r/acoilier/debian-sshd)

### Centos
images server accessible en ssh
- [acoilier/centos-sshd:8](https://hub.docker.com/r/acoilier/centos-sshd)
- [acoilier/centos-sshd:7](https://hub.docker.com/r/acoilier/centos-sshd)

## Informations sur les containeurs sshd
### Config

  - `PermitRootLogin yes`
  - `UsePAM no`
  - exposed port 22
  - default command: `/usr/sbin/sshd -D`
  - root password: `root`

### Exemple de test de connexion ssh sur un containeur

```bash
$ sudo docker run -d -P --name test_sshd acoilier/ubuntu-sshd:20.04
$ sudo docker port test_sshd 22
  0.0.0.0:37876

$ ssh root@localhost -p 37876
# Le mot de passe est `root`
root@test_sshd $

sudo docker stop test_sshd && sudo docker rm test_sshd
```


