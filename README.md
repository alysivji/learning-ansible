# Ansible

## Process

1. Create a VM and install your private key on it

`ssh-keygen -t rsa -b 4096`
`ssh-copy-id root@[ip]`

2. point to prviate key or add it using ssh-add, uses OpenSSH.

## Definitions

### Inventory File

- list of servers separated into roles?

### Playbook

- series of actions to run on specified groups of servers
- should be **idempotent**

```yaml
---
- hosts: [nginx]
  remote_user: webadmin
  tasks:
    - name: Ensure the NGINX daemon has started
      service: name=nginx state=started
      become: yes
      become_method: sudo
```

## Workflow

1. Run `ansible-playbook -i ./hosts playbook_init_config.yml`

--ask-pass
--key-file
https://stackoverflow.com/questions/44734179/specifying-ssh-key-in-ansible-playbook-file

## Resources

- [TalkPython course: Intro to Ansible](https://training.talkpython.fm/courses/details/introduction-to-ansible-with-python)
- [Ansible Examples](https://github.com/ansible/ansible-examples)
- [Ansible GitHub](https://github.com/ansible/ansible)
- [Ansible Docs](https://docs.ansible.com/)
- Ansible Docs: [Modules by Category](https://docs.ansible.com/ansible/latest/modules/modules_by_category.html)
