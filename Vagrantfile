Vagrant.configure("2") do |config|
  config.vm.synced_folder ".","/vagrant"
  #config.vm.synced_folder ".","/home/vagrant"
  config.vm.box = "ubuntu/xenial64"
  config.ssh.insert_key = false

 config.vm.provision "docker", type: "shell", inline: <<-SHELL
    echo "Updating ......."
    sudo apt-get update -y
    echo "Installing docker ..."
    sudo apt install docker.io -y

    echo "starting docker ..."
    sudo systemctl start docker
    sudo systemctl enable docker
    echo "checking docker version"
    docker --version
    SHELL


 config.vm.provision "ansible", type: "shell", inline: <<-SHELL
    echo "Updating ...."
    sudo apt update
    echo "Installing ansible ..."
    sudo apt install software-properties-common -y
    sudo apt-add-repository --yes --update ppa:ansible/ansible
    sudo apt install ansible -y
    SHELL
end
