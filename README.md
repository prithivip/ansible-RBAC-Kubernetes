This playbook will prompt for 

root@ansible:~/ansible/ansible-RBAC-Kubernetes# ansible-playbook ansible_rbac_for_kubernetes.yaml -i /root/ansible/inventory/kube_inventory 

[WARNING]: Invalid characters were found in group names but not replaced, use -vvvv to see details

Enter Username: bob

Enter Groupname: production

Enter Namespace: production

Enter Clustername: kubernetes

Enter ClusterAddress: 10.128.0.40

Enter the API Verb rules For New User Like (create,delete,update,patch,get,list,watch): create,delete,list,update,get 

Enter the API Resources For New User Like (pod,deployment,daemonset,statefulset,service): pod,deployment,service


PLAY [User Creation in K8s] ************************************************************************************

TASK [Creating Namespace If not exist] *************************************************************************

[WARNING]: conditional statements should not include jinja2 templating delimiters such as {{ }} or {% %}.

Found: "{{Namespace}}" is defined

changed: [kmaster]

TASK [Generating Private Key For New User] *********************************************************************

changed: [kmaster]

TASK [Creating CSR (Certificate Signing Request)] **************************************************************

changed: [kmaster]

TASK [Signing Newuser Certificate With K8s CA (Certificate Authorities)] ***************************************

changed: [kmaster]

TASK [Setting up kubeconfig for newuser] ***********************************************************************

changed: [kmaster]

TASK [Add User in Kubeconfig File] *****************************************************************************

changed: [kmaster]

TASK [Setting Up Context For New User] *************************************************************************

changed: [kmaster]

TASK [Creating Roles for New User] *****************************************************************************

changed: [kmaster]

TASK [Assigning Roles For New User] ****************************************************************************

changed: [kmaster]

TASK [Modifying User Context] **********************************************************************************

changed: [kmaster]

PLAY RECAP *****************************************************************************************************

kmaster                    : ok=10   changed=10   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
