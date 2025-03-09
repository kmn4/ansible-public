# ansible-public

## wsl.yml

``` powershell
wsl --install Debian
```

``` shell
sudo sh -c 'cat > /etc/wsl.conf' <<'EOS' && sudo apt update && sudo apt install -y dbus ansible git
[boot]
systemd=true
EOS
```

``` powershell
wsl -t Debian ; wsl -d Debian
```

``` shell
{ test -n "$become_pass" || read -sp 'sudo password: ' become_pass ; } && ( cd ~ && if [ ! -d ansible-public ] ; then git clone https://github.com/kmn4/ansible-public ; fi && cd ~/ansible-public && ansible-playbook wsl.yml -e "ansible_become_pass=$become_pass" -e "restricted_user=$(id -un)" -D ) && unset become_pass
```
