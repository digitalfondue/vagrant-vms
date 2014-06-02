vagrant-vms
===========

Vagrant VMs to test PostgreSQL and MySQL.

Under MIT License.

## Installation

* You need to have [Vagrant] installed.

* Check out this project:

        git clone https://github.com/digitalfondue/vagrant-vms.git
        
* Initialize the Puppet submodules:

        git submodule update –-init
        
* In the Vagrantfile change `'db' => 'testdb'` to a proper name for your DB.

* Run `vagrant up` from the base directory of this project to initialize the VMs (this may take some time because the first time it has to download the base box image).

## Known bug

Under windows, if the automatic crlf conversion is set to true (most likely), the puppet pgsql submodule is broken. You can manually fix it running `dos2unix validate_postgresql_connection.sh`

## Usage

You can use `vagrant up` to boot every VM in the Vagrantfile or just `vagrant up pgsql` / `vagrant up mysql` if you need a specific database.

### Connect to the PostgreSQL VM

The VM uses PostgreSQL 9.1 (on port 5432), has a superuser `postgres` with password `password` and creates a DB named `testdb`.

This is how a JDBC connection string looks like:

`jdbc:postgresql://localhost:5432/testdb?user=postgres&password=password`

###Connect to the MySQL VM

The VM uses MySQL 5.5 (on port 3306), the `root` user doesn't have a password and creates a DB named `testdb`.

This is how a JDBC connection string looks like:

`jdbc:mysql://localhost:3306/testdb`



[Vagrant]: http://www.vagrantup.com/
