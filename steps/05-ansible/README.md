# Ansible (configuration management)

[Fast tutour](https://www.ansible.com/quick-start-video)

[Modules list](http://docs.ansible.com/ansible/list_of_all_modules.html)

```
sudo chmod a+rwx /var/run/docker.sock

d build -t box .
d run -d --name box-1 --label group=app box
d run -d --name box-2 --label group=app box
chmod 600 secure/id_rsa
eval $(ssh-agent)
ssh-add secure/id_rsa

ansible app -u root -i ./inv -m ping 
# module

ansible-doc ping
ansible-doc -l | less

ansible app -u root -i ./inv -m setup  | less
ansible app -u root -i ./inv -m file -a 'path=/etc/hosts'

ansible app -u root -i ./inv -m copy -a "content=hello dest=/tmp/hello"
ansible app -u root -i ./inv -m shell -a "cat /tmp/hello"


ansible app -u root -i ./inv -m file -a 'path=/tmp/hello'
ansible app -u root -i ./inv -m file -a 'path=/tmp/hello state=absent'
ansible app -u root -i ./inv -m file -a 'path=/tmp/hello'


ansible app -u root -i ./inv -m file -a 'path=/tmp/hello'

ansible-playbook  -i ./inv play.yml

ansible app -u root -i ./inv -m shell -a "cat /tmp/myfile.txt" 

```
