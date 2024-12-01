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


Verification steps:

==================

On Master node

Using certificate :

==================

cd /etc/kubernetes/users/certificates

kubectl config view

kubectl config get-contexts

kubectl config set-context bob --user=bob --cluster=kubernetes

kubectl config set-credentials bob --client-key=bob.key --client-certificate=bob.crt --embed-certs

kubectl config use-context bob

kubectl config get-contexts

kubectl auth can-i create deployments --namespace production

kubectl run nginx --image nginx -n production

kubectl get pods -n production

kubectl config use-context kubernetes-admin@kubernetes

Impersonate from kubernetes admin user :

kubectl auth can-i list secrets --namespace production --as bob


Using kubeconfig :[No config context switch is needed]

==================

kubectl --kubeconfig bob.kubeconfig get pod -n production

kubectl --kubeconfig bob.kubeconfig get secrets -n production

kubectl --kubeconfig bob.kubeconfig create deployment webserver --replicas=2 --image=nginx:alpine

kubectl --kubeconfig bob.kubeconfig get pod -n production




