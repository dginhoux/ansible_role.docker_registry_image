ginhouxnet.sysctl
=========

This ansible role is used to synchronize docker image from public registries and push them in a local registry.
Docker need to be installed on the node where this roles is running.


Requirements
------------

This ansible role will only run on identified OS defined on meta/main.yml


Role Variables
--------------


```
docker_hub_login: "aaa"
docker_hub_password: "aaa"

docker_cache_registry: "localhost:5000"

docker_images_list:
  - { state: "absent", name: "adminer", tag: "4.8.0-standalone" }

```

Dependencies
------------




Example Playbook
----------------



License
-------

BSD


Author Information
------------------

Dany GINHOUX
