# mariadb_vagrant_libvirt_ansible

This Vagrant setup creates a VM and configures [a MariaDB
server](https://mariadb.org/).
It also creates a VM and installs the `mariadb` client command, that allows a
user to connect to a MariaDB database.

Default OS is openSUSE Leap 15.6. Although that can be changed in the
Vagrantfile, please beware that this will break the Ansible provisioning.

## Vagrant

1. You need vagrant obviously. And ansible. And git...
1. Fetch the box, per default this is `opensuse/Leap-15.6.x86_64`, using
   `vagrant box add opensuse/Leap-15.6.x86_64`.
1. Make sure the git submodules are fully working by issuing `git submodule init
   && git submodule update`
1. Run `vagrant up`
1. Log in on the `mariadb-client` VM using `vagrant ssh mariadb-client`.
1. You can find the commands to connect to your database server in the
   `mariadb_snippet.txt` file. Ansible also printed the commands and the
   passwords at the end of the provisioning.
1. Running the command using the `example-user` will work, while the connection
   using the `root` user will fail. As is good security practice, the root user
   is only allowed to connect from the server machine itself, using `localhost`.
   Of course this can be changed, but this is left as an exercise for you... :-)

   Note: Contrary to the behaviour for PostgreSQL, the `root` user will be
   denied **after** the password prompt.
1. Party!

## Cleaning up

The VMs can be torn down after playing around using `vagrant destroy`.

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via git@johannes-kastl.de
