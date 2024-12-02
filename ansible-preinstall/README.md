Run ansible

```bash
ansible-playbook -i inventory/servers.ini servers.yaml --become --become-method=sudo
```

