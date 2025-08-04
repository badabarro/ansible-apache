Vagrant.configure("2") do |config|

  # Machine Ansible Master (Ubuntu)
  config.vm.define "ansible-master" do |ansible|
    ansible.vm.box = "ubuntu/bionic64"
    ansible.vm.hostname = "ansible-master"
    ansible.vm.network "private_network", ip: "192.168.56.5"

    # Ajout du dossier de clés privées hôte monté dans la VM
    ansible.vm.synced_folder "C:/Users/Admin/.vagrant.d/insecure_private_keys", "/home/vagrant/insecure_keys", type: "virtualbox"


    # Provisionnement : installer ansible
    ansible.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y software-properties-common
      sudo apt-add-repository --yes --update ppa:ansible/ansible
      sudo apt-get install -y ansible
    SHELL

    # Copy de la clé SSH Vagrant pour se connecter aux cibles
    # (à adapter selon ta config)
    ansible.vm.provision "shell", inline: <<-SHELL
      mkdir -p /home/vagrant/.ssh
      cp /vagrant/.vagrant/machines/ubuntu-server/virtualbox/private_key /home/vagrant/.ssh/id_rsa_ubuntu
      cp /vagrant/.vagrant/machines/centos-server/virtualbox/private_key /home/vagrant/.ssh/id_rsa_centos
      chmod 600 /home/vagrant/.ssh/id_rsa_*
      chown -R vagrant:vagrant /home/vagrant/.ssh
    SHELL
  end

  # Machine Ubuntu cible
  config.vm.define "ubuntu-server" do |ubuntu|
    ubuntu.vm.box = "ubuntu/bionic64"
    ubuntu.vm.hostname = "ubuntu-server"
    ubuntu.vm.network "private_network", ip: "192.168.56.10"
  end

  # Machine CentOS cible
  config.vm.define "centos-server" do |centos|
    centos.vm.box = "centos/7"
    centos.vm.hostname = "centos-server"
    centos.vm.network "private_network", ip: "192.168.56.11"
  end

end

