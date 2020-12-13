ansible-playbook -i inventory k8s_init.yml

kubectl apply -f https://raw.githubusercontent.com/mrFlick72/ansible-playground/master/kubernetes-sample/legacy-webapp.yml



ssh 10.10.10.100 -i ~/.vagrant.d/insecure_private_key


sudo kubeadm init --apiserver-advertise-address=10.10.0.10 --pod-network-cidr=10.244.0.0/16 

kubeadm init --apiserver-advertise-address="192.168.100.10" --apiserver-cert-extra-sans="192.168.100.10" --pod-network-cidr=192.168.0.0/16
 kubectl create -f https://docs.projectcalico.org/v3.4/getting-started/kubernetes/installation/hosted/calico.yaml

http://10.10.0.11:31305/very-legacy-webapp/webapp/index.jsp

192.168.x
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml 
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.30.0/deploy/static/mandatory.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.30.0/deploy/static/provider/baremetal/service-nodeport.yaml

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config


sudo systemctl daemon-reload
sudo systemctl restart kubelet