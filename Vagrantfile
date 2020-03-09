Vagrant.configure("2") do |config|

  config.vm.box =  "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |vb|

    vb.cpus = "1"
    vb.memory = "2048"

  end

  config.ssh.insert_key = false
  config.vm.provision "file", source: "./id_rsa.pub", destination: "~/.ssh/authorized_keys"
  config.ssh.private_key_path = ["./id_rsa", "~/.vagrant.d/insecure_private_key"]

  config.vm.define "master" do |master|

    master.vm.network "private_network", ip: "192.168.33.10"
    master.vm.hostname = "master"

  end

  config.vm.define "node01" do |node01|

    node01.vm.network "private_network", ip: "192.168.33.20"
    node01.vm.hostname = "node01"

  end

  config.vm.define "node02" do |node02|

    node02.vm.network "private_network", ip: "192.168.33.30"
    node02.vm.hostname = "node02"

  end

end