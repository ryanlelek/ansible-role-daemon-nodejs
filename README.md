Daemon - Node.js
================

Run Node.js process as a Daemon with Upstart (moving to Systemd soon)

Requirements
------------

Required:  
- Node.js (via role: nodesource.node)

Recommended:
- Git (via role: ryanlelek.packages)

Role Variables
--------------

- **daemon_name**: nodejs_daemon
- **daemon_command**: npm start
- **daemon_envvars**: []
- **npm_token**: false

Dependencies
------------

- nodesource.node

Example Playbook
----------------

    # Run as Root
    - hosts: all
      become: yes
      roles:
        - ryanlelek.packages
        - nodesource.node

    # Run as User
    - hosts: all
      roles:

        # Clone a Node.js Git repository
        - role: ryanlelek.git-repo
          git_repo_name: raneto
          git_repo_url: https://github.com/gilbitron/Raneto.git

        # Daemonize
        # Runs `make deploy` beforehand
        - role: ryanlelek.daemon-nodejs
          daemon_name: raneto
          daemon_command: npm start
          daemon_envvars:
            - { key: NODE_ENV, value: PRODUCTION }
            - { key: PORT,     value: 3000 }

License
-------

MIT

Author Information
------------------

Created by [Ryan Lelek](https://www.ryanlelek.com)  
Part of [AnsibleTutorials.com](http://www.ansibletutorials.com)
