Ansible playbook to install example apps for GPTE 3scale courses


### Installation of Coolstore Products API

#### Prerequisites
* OCP 4.6.x cluster
* Cluster admin access
* `oc` OpenShift CLI tool
* Ansible 2.9.x with Kubernetes `k8s` module installed

#### Installation of Coolstore Products API

* Make sure you are logged in into the cluster as cluster administrator.
* Change directory to the `ansible` directory.
* Copy the `inventories/inventory.template` inventory file:
  ```
  $ cp inventories/inventory.template inventories/inventory
  ``` 
* Complete the inventory file. Pay attention to the following parameters:
  * **start_user**, **end_user**: First and last sequence number. The sequence number is appended to **user_base_name**. The Products API will be installed once for each user within the selected sequence.
  * **business_service_namespace**: The Products API will be installed in the {{ ocp_user }}-{{ business_service_namespace }} namespace.

* Run the installation playbook:
  ```
  $ ansible-playbook -i inventories/inventory playbooks/products_api.yml
  ```