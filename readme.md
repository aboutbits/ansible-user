Ansible User Role
=================

User creation role.

## Role Variables

- `user_name`: The name of the user
- `user_password`: The password for the user
- `user_groups`: The groups of the user
- `user_authorized_keys`: The authorized keys of the user

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: ansible-user
      vars:
        user_name: alex
        user_password: sha512-hashed-password
        user_groups:
          - docker
        user_authorized_keys:
          - {{ lookup('file', 'path-to-key') }}
```

## Password

To create a password hash for a user, the following command must be extecuted:

```
mkpasswd --method=SHA-512
```

The command is contained within the package "whois" that can be installed on
Linux by executing `apt-get install -y whois`.

## Versioning

In order to have a verioning in place and working, create leightweight tags that point to the appropriate minor release versions.

Creating a new minor release:

```bash
git tag 1.0
git push --tags
```

Replacing an already existing minor release:

```bash
git tag -d 1.0
git push origin :refs/tags/1.0
git tag 1.0
git push --tags
```
