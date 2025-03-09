``` shell
read -sp "sudo password: " become_pass &&
ansible-playbook wsl.yml -e "ansible_become_pass=$become_pass" -e "restricted_user=$(id -un)" -DC
```
