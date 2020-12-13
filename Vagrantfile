# -*- mode: ruby -*-
# vi: set ft=ruby :

cluster = {
  "master" => { :ip => "10.10.0.10", :cpus => 2, :mem => 2048 , :disksize => "10GB", :playbook => "k8s_installation.yml"},
  "worker1" => { :ip => "10.10.0.11", :cpus => 2, :mem => 2048 , :disksize => "10GB", :playbook => "k8s_installation.yml"},
  "worker2" => { :ip => "10.10.0.12", :cpus => 2, :mem => 2048 , :disksize => "10GB", :playbook => "k8s_installation.yml"},
  "balancer" => { :ip => "10.10.10.100", :publicIp => "10.10.100.100", :cpus => 1, :mem => 1024 , :disksize => "10GB", :playbook => "nginx.yml"}
}


Vagrant.configure("2") do |config|
  cluster.each_with_index do |(hostname, info), index|
    config.vm.define hostname do |cfg|
        config.vm.box = "centos/8"
        config.ssh.insert_key = false
        unless #{info[:publicIp].nill?}
          cfg.vm.network "public_network", ip: "#{info[:publicIp]}", bridge: "eno2"
        end

        cfg.vm.network "private_network", ip: "#{info[:ip]}"
        cfg.disksize.size = "#{info[:disksize]}"
        cfg.vm.hostname = hostname

        cfg.vm.provider "virtualbox" do |vb|
          vb.memory = "#{info[:mem]}"
          vb.cpus =  "#{info[:cpus]}"
        end

        cfg.vm.provision :ansible do |ansible|
          ansible.playbook = "#{info[:playbook]}"
          ansible.extra_vars = {
                node_ip: "#{info[:ip]}"
            }
        end
    end
  end

end