Vagrant.configure("2") do |config|

    config.vm.box =  "ubuntu/bionic64"

    config.ssh.insert_key = false
    config.vm.provision "file", source: "./id_rsa.pub", destination: "~/.ssh/authorized_keys"
    config.ssh.private_key_path = ["./id_rsa", "~/.vagrant.d/insecure_private_key"]

    config.vm.provider "virtualbox" do |vb|
      vb.cpus = "1"
      vb.memory = "1024"
    end

    N = 3
    (1..N).each do |machine_id|
      config.vm.define "machine#{machine_id}" do |machine|
        machine.vm.hostname = "machine#{machine_id}"
        machine.vm.network "private_network", ip: "192.168.33.#{9+machine_id}"

        if machine_id == 1
          machine.vm.provider "virtualbox" do |vb|
            vb.cpus = "2"
            vb.memory = "2048"
          end
        end

        if machine_id == N
          machine.vm.provision :ansible do |ansible|
            ansible.playbook = "main.yml"
            ansible.inventory_path = "hosts"
            ansible.limit = "all"
          end
        end

      end
    end

end