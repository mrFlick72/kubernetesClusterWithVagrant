# Vagrant Setup

In order to custumize your k88 cluster edit the Vagrantfile to add or remove nodes as you wish. After that run this comand to ask to Vagrant to provision 
your vagrant machine and run the k8s_init playbook in order to run the final step to configure your cluster

```
vagrant up && ansible-playbook -i inventory k8s_init.yml
``

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