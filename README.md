## Usage

You should already have [Vagrant](http://vagrantup.com/) installed.

Then edit the Vagrantfile to uncomment the application name part, to put your project very own name.
After that simply run

```bash
vagrant up
```

Note: if you already have a service using the port 8080, or if you have already use this repository to create an other symfony2 project, you need to the Vagrantfile to chose an other port than 8080, then run `vagrant up`

it will install, using Ansible for the provisionning: 

  * Apache2
  * php-fpm
  * php-cli
  * postgresql OR mysql server (depending on the `DBTYPE` variable declared in the Vagrantfile)
  * composer
  * symfony2

You can then go in your virtual machine using `vagrant ssh` and your project's files will be accessible in `/vagrant/your_application_name`. From there you can run composer to install any new additional dependencies you will add, or run the `php app/console ....` of symfony2.

To open the website itself, you simply need to open `localhost:8080` (if you changed the port, of course replace 8080) in your browser.

## Starting off a new project

Using this template for starting a new Symfony webapp project from scratch, a typical workflow could resemble something like the following:
 1. Initialize a new empty git repo for your project, let's say it is at `http://gitlab.local/projects/my-app-repo.git/
 2. Clone it into a working copy, thereby setting it's `origin` remote: `cd ~/Projects/; git clone http://gitlab.local/projects/my-app-repo.git/; cd my-app-repo/`
 3. Merge a remote branch originating from this template repo, e.g. `git remote add -t master github-base https://github.com/we-bridge/vagrant-ansible-symfony.git ; git fetch gh-base; git merge gh-base/master` or simply `git pull https://github.com/we-bridge/vagrant-ansible-symfony.git`
 4. (optional) If the previous commit log bothers you, replace it all with a single commit before doing anything else: `git reset $(git commit-tree HEAD^{tree} -m "Initialized from template")`

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

If you want to replace apache2, by say Nginx, you can still use this repository and simply add an additional role to the provisioning. Pull Request / Patches are welcome.

