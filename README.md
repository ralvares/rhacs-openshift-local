# Deploy Red Hat Advanced Cluster Security for Kubernetes Demo ( Workloads and Pipelines ) on RedHat OpenShift local

## PREREQUISITES

- RedHat OpenShift local - Formerly Red Hat CodeReady Containers [Getting Started Guide](https://access.redhat.com/documentation/en-us/red_hat_openshift_local/2.5/html-single/getting_started_guide/index#doc-wrapper)
- Python Libraries
  - pyyaml
  - jmespath
  - openshift
  - ansible 2.9 or later
- Ansible Collection
  - kubernetes.core

#### Minimum Requirements to run the demo workload on top of OpenShift Local: [Configuring the virtual machine](https://access.redhat.com/documentation/en-us/red_hat_openshift_local/2.5/html-single/getting_started_guide/index#changing-the-selected-preset_gsg)

- Minimum 4 vCPU (additional are strongly recommended).
- Minimum 16 GB RAM (additional memory is strongly recommended).

### Steps

#### Configuring the CRC Virtual Machine
---
```
crc config set cpus 4
crc config set memory 16384
```

#### Installing RHACS and Demo Workloads
---

##### Install EPEL on CentOS
```
yum install epel-release -y
```

##### Install the python3 libraries - Centos/RHEL
```
yum install python3-pyyaml python3-jmespath python3-openshift ansible -y
```

##### Install the python3 libraries - MacOS
```
brew install python
pip3 install ansible
pip3 install pyyaml openshift jmespath
```

##### Install ansible collection
```
ansible-galaxy collection install kubernetes.core
```

##### Install RHACS and Demo Workloads
```
git clone https://github.com/ralvares/rhacs-openshift-local
cd rhacs-openshift-local
```

Login to crc/ocp using a Cluster-Admin user.
---
```
oc login -u kubeadmin https://api.crc.testing:6443 
```

Running the playbook.
---
```
ansible-playbook rhacs-install.yaml
```

It might take a bit of time, so grab a coffee and enjoy :)