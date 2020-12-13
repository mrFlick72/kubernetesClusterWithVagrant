# Vagrant Setup

In order to custumize your k8s cluster edit the Vagrantfile to add or remove nodes as you wish. 
After that run this comand to ask to Vagrant to provision your vagrant machine and run the k8s_init playbook in order to run the final step to configure your cluster. The command is below:

```
vagrant up && ansible-playbook -i inventory k8s_init.yml
```

### tips
In case of network clash, don't worry you can change from vagrant all the needed.
Right now pay attention to edit accordingly the Ansible inventory file in the repo

# Sample Applications
If you are interested to test the environment you can choose a simple app like below:

``` bash
https://raw.githubusercontent.com/mrFlick72/ansible-playground/master/kubernetes-sample/legacy-webapp.yml
```

or some thing of more complex like below
``` bash
kubectl apply -f https://raw.githubusercontent.com/mrFlick72/spring-cloud-kubernetes-demo/master/docker/kubernetes/mongo.yml
kubectl apply -f https://raw.githubusercontent.com/mrFlick72/spring-cloud-kubernetes-demo/master/docker/kubernetes/redis.yml
kubectl apply -f https://raw.githubusercontent.com/mrFlick72/spring-cloud-kubernetes-demo/master/docker/kubernetes/hello-service.yml
kubectl apply -f https://raw.githubusercontent.com/mrFlick72/spring-cloud-kubernetes-demo/master/docker/kubernetes/message-service.yml
kubectl apply -f https://raw.githubusercontent.com/mrFlick72/spring-cloud-kubernetes-demo/master/docker/kubernetes/ui-interface.yml
```

then you can use a balancer already configured during the init process on this ip `10.10.10.100`.