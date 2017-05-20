Building Kubernetes Cluster using Ansible Playbooks.
-------------------------------------------

These playbooks require Ansible 1.9.

This playbook sets up your nodes and installs Kubernetes on them using Kargo. The inventory file
'hosts' defines the nodes in which the stacks should be configured.

        [all]
        k8s-node-01
        k8s-node-02
        k8s-node-03

Before running install the Ansible Galaxy roles using `ansible-galaxy`:

		ansible-galaxy --roles-path galaxy-roles/ install -r requirements.yml

On setting up a brand new server, the stack can be deployed using the following command:
		
		ansible-playbook -i inventories/production/hosts pre-install.yml -e 'first_run=1' -k

Upon subsequent runs, the stack can be deployed / updated using the following command:

		ansible-playbook -i inventories/production/hosts pre-install.yml

After the `pre-install.yml` playbook has run you can run the `post-install.yml` playbook:

		ansible-playbook -i inventories/production/hosts post-install.yml
