# Ansible playbook for Ubuntu on odroid XU4 - basic config, Docker, Kubernetes, Dashboard and Traefik.

This repository contains playbooks to configure a cluster of [odroid XU4](http://www.hardkernel.com/main/products/prdt_info.php?g_code=G143452239825) devices.

The odroids have a basic Ubuntu 16.04 LTS installation, DHCP reserved addresses and the names ready in the DNS server.

### Base install
The base_docker_install playbook installs some basic stuff and the latest Docker version on a 5 node cluster, if you're plan is to only use Docker this could be enough for you.

### Kubernetes
The install_kubernetes playbook is heavily based on the [rhuss](https://github.com/Project31/ansible-kubernetes-openshift-pi3) Pi3 cluster setup and installs and configures Kubernetes, it will downgrade Docker to the latest supported version for Kubernetes.

### Tools
The tools playbook adds some handy tools to manage the Kubernetes cluster, it adds the Kubernetes Dashboard and makes it available via Traefik.

### Reset Kubernetes
You can use the kubernetes_reset playbook to reset the Kubernetes installation when needed, example when you run into issues after testing some stuff (looks at self).

### Tips
+ When you see an error that looks something like this `User "system:serviceaccount:kube-system:default" cannot list replicationcontrollers in the namespace "default".` in the Dashboard after deployment, you can resolve it by giving the service account the necessary rights:

`kubectl create clusterrolebinding --user system:serviceaccount:kube-system:kubernetes-dashboard system-cluster-admin --clusterrole cluster-admin`

This is not for production though, purely for lab environments as it is not the most secure way to dealing with it.

+ If you're planning to use these playbooks don't forget to adjust the hosts file to your own hostnames or ip-addresses.

### Notes
These playbooks were used with Ansible version 2.4.2.0
