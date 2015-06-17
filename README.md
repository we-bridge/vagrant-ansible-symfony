## Usage

You should already have [Vagrant](http://vagrantup.com/) installed.

Then edit the VagrantFile to uncomment the application name part, to put your project very own name.
After that simply run

```bash
vagrant up
```

Note: if you already have a service using the port 8080, or if you have already use this repository to create an other symfony2 project, you need to the Vagrantfile to chose an other port than 8080, then run `vagrant up`

it will install, using Ansible for the provisionning: 

  * Apache2
  * php-fpm
  * php-cli
  * postgresql
  * composer
  * symfony2

You can then go in your virtual machine using `vagrant ssh` and your project's files will be accessible in `/vagrant/your_application_name`. From there you can run composer to install any new additional dependencies you will add, or run the `php app/console ....` of symfony2.

To open the website itself, you simply need to open `localhost:8080` (if you changed the port, of course replace 8080) in your browser.

### Checking out existing projects
Usually `composer install` is run automatically during provisioning. However, if for some reason (network problems? Github API limits?) this step fails, your project will typically generate errors related to `PHP Fatal error:  require_once(): Failed opening required '(...)/app/bootstrap.php.cache'` etc, since the cache bootstrap file is built during composer's post-install step. If this happens, simply re-run either `vagrant provision` or `composer install` manually once to fix up these issues.

## Requirements

  * ansible > 1.6

Note: on ubuntu 14.04 you have to install ansible with `pip` rather than `apt-get`
or if you don't want to use `pip` to install system-wide commands, you can install ansible PPA

```
apt-get install python-software-properties
add-apt-repository ppa:ansible/ansible
apt-get update
apt-get install ansible
```

## Customization

If you want to replace apache2, by say Nginx, or Postgresql by Mysql, you can still use this repository, and simply add an other role in the provisionning. Pull Request / Patches are welcome.
