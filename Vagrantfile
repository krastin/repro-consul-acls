# -*- mode: ruby -*-
# vi: set ft=ruby :

consul_servers = 5
vault_servers = 1

Vagrant.configure("2") do |config|

  # Consul servers
  (1..consul_servers).each do |i|
    config.vm.define "consul0#{i}" do |consul|
      consul.vm.hostname = "consul0#{i}"
      consul.vm.box = "krastin/xenial-consul"
      consul.vm.network "private_network", ip: "10.10.10.#{110+i}"
      consul.vm.provision "shell", path: "https://raw.githubusercontent.com/krastin/hashistack-provisioning/master/consul/install/install_consul.sh"
      consul.vm.provision "shell", path: "https://raw.githubusercontent.com/krastin/hashistack-provisioning/master/consul/configure/configure_consul.sh",
      env: {
        "NODE_NAME" => "consul0#{i}",
        "RETRYIPS" => "10.10.10.111", # this could be better
        "SERVER" => "true",
        "BOOTSTRAP" => "3",
        "LOCAL_IP" => "10.10.10.#{110+i}",
      }
    end
  end
end
