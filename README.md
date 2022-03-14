# ansible-role-dotfiles

Confguration of dotfiles on a Linux based environment

- Installs RCM
- Clone dotfile repository
- Create symlinks via rcup
- Create global .gitconfig

## Test

Run `molecule test` for testing this role via Docker

## Requirements

## Role Variables

| Variable                           | Description                           | default                                     |
| ---------------------------------- | ------------------------------------- | --------------------------------------------|
| dotfiles_repo_url                  | URL of repo to clone for use with RCM | https://github.com/floatingman/dotfiles.git |
| gitconfig.name                     | Name of global git config             | Daniel                                      |
| gitconfig.username                 | Username of global git config         | floatingman                                 |
| gitconfig.mail                     | Mail of global git config             | dan@danlovesprogramming.com                 |
| gitconfig.credential_cache         | Cache git credentials                 | true                                        |
| gitconfig.credential_cache_timeout | How long to store git credentials     | 3600                                        |
| gitconfig.delta                    | Use delta as git diff enhancement     | true                                        |
| gitconfig.neovim_remote            | Use NeoVim as global diff tool        | true                                        |

## Dependencies

- ansible-role-basic

## Example Playbook

```
---
- name: Playbook
  hosts: localhost
  connection: local
  pre_tasks:
    - set_fact:
        dotfiles_path: "{{ ansible_env.HOME }}/.dotfiles"
        gitconfig:
          name: infratest
          username: test
          mail: max.mustermann@example.com
          credential_cache: "false"
          credential_cache_timeout: 600
          delta: "false"
          neovim_remote: "false"
  roles:
    - ansible-role-dotfiles
```

## License

MIT
