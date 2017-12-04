# Ansible playbook for Ubuntu on odroid XU4 - basic config and Docker (for now).

Decided to put my playbooks online for safe keeping. This playbook configures a basic Ubuntu 16.04 LTS and installs Docker on a 5 node [odroid XU4](http://www.hardkernel.com/main/products/prdt_info.php?g_code=G143452239825) cluster.

Plan is to expand the playbooks over time, add Kubernetes for example.

If you're looking to use this playbook as is, just clone the repo and run:

```ansible-playbook -i hosts ansible_odroid.yml [--ask-become-pass]```

Of course don't forget to adjust the hosts file to your own hostname or ip-address.
