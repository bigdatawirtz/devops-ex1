# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
    
  # Identifica a imaxe/box de vagrant que vas utilizar: "ubuntu/focal64"
  config.vm.box = "ubuntu/focal64"
    
  # Indica o nome do hostname
  config.vm.hostname = "docker-host"

  config.vm.provision "shell", inline: <<-SHELL

    apt-get update
    apt-get install -y ca-certificates curl gnupg lsb-release
    mkdir -m 0755 -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

    apt-get update
    apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    groupadd docker
    usermod -aG docker vagrant

   SHELL
end
