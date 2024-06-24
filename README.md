# ansible_practice
requirements installation:

ansible-galaxy role install -r requirements.yml --ignore-certs

ansible-galaxy collection install -r requirements.yml --ignore-certs

---

roles:

postgresql

nginx

xpaste-app

---

vars:

./vars_unencrypted.yml

./roles/xpaste-app/vars/main.yml

./sudopass_unencrypted.yml

---

inventory:

./hosts.ini

---

setting ssh keys:

./keys/ssh-key (private key for ansible ssh connection to nodes)

./roles/xpaste-app/files/.ssh/ (ssh files for app git, names must correspond to values in ./roles/xpaste-app/vars/main.yml) 


---

setting secrets:

ansible-vault create sudopass.yml

-or-

ansible-vault encrypt vars.yml

-or-

ansible-vault encrypt --vault-id xpaste-vars@prompt vars.yml

---

running playbook:

ansible-playbook playbook.yml -vvv  --extra-vars '@sudopass_unencrypted.yml'

-or-

ansible-playbook playbook.yml -vvv --ask-vault-pass --extra-vars '@sudopass_encrypted.yml'

---
