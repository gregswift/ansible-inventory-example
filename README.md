This repository is a basic example of how i currently think about static ansible inventories. The full group interection capabilities works really well when you have playbooks that should work across lots of different systems.

# Examples
Here are some samples that work with it

## All hosts (the baseline)
```
$ ansible all -i inventory/ --list-hosts
  hosts (52):
    tool2-n01.jenkins.lon.rackspace.net
    tool2-n02.jenkins.lon.rackspace.net
    tool2-n03.jenkins.lon.rackspace.net
    tool2-n04.jenkins.lon.rackspace.net
    securitah-n01.jenkins.lon.rackspace.net
    securitah-n02.jenkins.lon.rackspace.net
    securitah-n03.jenkins.lon.rackspace.net
    securitah-n04.jenkins.lon.rackspace.net
    app1-api-n01.lon.prod.example.com
    app1-api-n02.lon.prod.example.com
    app1-api-n03.lon.prod.example.com
    app1-api-n01.ord.prod.example.com
    app1-api-n02.ord.prod.example.com
    app1-api-n03.ord.prod.example.com
    app2-api-n01.lon.prod.example.com
    app2-api-n02.lon.prod.example.com
    app2-api-n03.lon.prod.example.com
    app2-api-n01.ord.prod.example.com
    app2-api-n02.ord.prod.example.com
    app2-api-n03.ord.prod.example.com
    app1-api-n01.lon.staging.example.com
    app1-api-n02.lon.staging.example.com
    app1-api-n03.lon.staging.example.com
    app1-api-n01.ord.staging.example.com
    app1-api-n02.ord.staging.example.com
    app1-api-n03.ord.staging.example.com
    app2-api-n01.lon.staging.example.com
    app2-api-n02.lon.staging.example.com
    app2-api-n03.lon.staging.example.com
    app2-api-n01.ord.staging.example.com
    app2-api-n02.ord.staging.example.com
    app2-api-n03.ord.staging.example.com
    app1-n02.jenkins.lon.rackspace.net
    app1-n03.jenkins.lon.rackspace.net
    app1-n04.jenkins.lon.rackspace.net
    app1-db-n01.lon.prod.example.com
    app1-db-n02.lon.prod.example.com
    app2-db-n01.lon.prod.example.com
    app2-db-n02.lon.prod.example.com
    app1-n01.jenkins.lon.rackspace.net
    app1-db-n01.lon.staging.example.com
    app1-db-n02.lon.staging.example.com
    app2-db-n01.lon.staging.example.com
    app2-db-n02.lon.staging.example.com
    app1-db-n01.ord.prod.example.com
    app1-db-n02.ord.prod.example.com
    app2-db-n01.ord.prod.example.com
    app2-db-n02.ord.prod.example.com
    app1-db-n01.ord.staging.example.com
    app1-db-n02.ord.staging.example.com
    app2-db-n01.ord.staging.example.com
    app2-db-n02.ord.staging.example.com
```

## Just staging
```
$ ansible all -i inventory/ --list-hosts -l staging
  hosts (20):
    app1-api-n01.lon.staging.example.com
    app1-api-n02.lon.staging.example.com
    app1-api-n03.lon.staging.example.com
    app1-api-n01.ord.staging.example.com
    app1-api-n02.ord.staging.example.com
    app1-api-n03.ord.staging.example.com
    app2-api-n01.lon.staging.example.com
    app2-api-n02.lon.staging.example.com
    app2-api-n03.lon.staging.example.com
    app2-api-n01.ord.staging.example.com
    app2-api-n02.ord.staging.example.com
    app2-api-n03.ord.staging.example.com
    app1-db-n01.lon.staging.example.com
    app1-db-n02.lon.staging.example.com
    app2-db-n01.lon.staging.example.com
    app2-db-n02.lon.staging.example.com
    app1-db-n01.ord.staging.example.com
    app1-db-n02.ord.staging.example.com
    app2-db-n01.ord.staging.example.com
    app2-db-n02.ord.staging.example.com

```

## App1 api nodes in lon prod
```
$ ansible all -i inventory/ --list-hosts -l 'app1:&api:&prod:&lon'
  hosts (3):
    app1-api-n01.lon.prod.example.com
    app1-api-n02.lon.prod.example.com
    app1-api-n03.lon.prod.example.com
```
or
```
$ ansible api -i inventory/ --list-hosts -l 'app1:&prod:&lon'
  hosts (3):
    app1-api-n01.lon.prod.example.com
    app1-api-n02.lon.prod.example.com
    app1-api-n03.lon.prod.example.com
```

## All jenkins masters
```
$ ansible jenkins -i inventory --list-hosts -l 'master'
  hosts (3):
    app1-n01.jenkins.lon.rackspace.net
    securitah-n01.jenkins.lon.rackspace.net
    tool2-n01.jenkins.lon.rackspace.net
```