# Linux Nginx MariaDB PHP on Vagrant Provision by Ansible

## Base VagrantBox
- https://github.com/tsuttsu305/Create-CentOS7-Virtualbox-VagrantBox

## Ansible Roles
- Add epel, remi repository
- Disabled SELinux
- Create Vagrant cache plugin using directory
- Insert Vagrant Insecure Key to authorized_key
- Install @Base "@Development tools"
- Install WebDevelopment Soft
    - Nginx
    - Mariadb-server
    - PHP-FPM
        - php-cli
        - php-intl
        - php-mbstring
        - php-pdo
        - php-gd
        - php-mcrypt
        - php-pear
        - php-xml
        - php-xmlrpc
        - php-mysqlnd
        - php-soap
        - php-devel
- Setting web-server (See Provisioning/group_vars/all file)
- Firewalld setting