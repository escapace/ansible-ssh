<p align="right">
    <a href="https://travis-ci.org/epiloque/ansible-ssh">
        <img src="https://travis-ci.org/epiloque/ansible-ssh.svg?branch=master"
             alt="build status">
    </a>
        <a href="https://galaxy.ansible.com/epiloque/ssh">
        <img src="https://img.shields.io/badge/ansible--galaxy-ssh-blue.svg"
             alt="ansible galaxy">
    </a>
</p>

ssh role

## Role Variables

Available variables are listed below, along with default values:

```yaml
ssh_keyboard_interactive_group:
```

## Example Playbook

```yaml
- hosts: servers
  roles:
    - epiloque.ssh
```

## License

BSD
