IMAGE_NAME = "ubuntu/xenial64"
N = 2

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
      
    config.vm.define "k8s-master" do |master|
        master.vm.provider "virtualbox" do |v|
            v.memory = 4096
            v.cpus = 2
        end
        master.vm.network :public_network
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "10.120.50.10"
        master.vm.hostname = "k8s-master"
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "kubernetes-setup/master-playbook.yml"
            ask_become_pass = true
            ansible.extra_vars = {
                node_ip: "10.120.50.10",
            }
        end
    end

    (1..N).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.provider "virtualbox" do |v|
                v.memory = 2048
                v.cpus = 2
            end
            node.vm.box = IMAGE_NAME
            node.vm.network "private_network", ip: "10.120.50.#{i + 10}"
            node.vm.hostname = "node-#{i}"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "kubernetes-setup/node-playbook.yml"
                ask_become_pass = true
                ansible.extra_vars = {
                    node_ip: "10.120.50.#{i + 10}",
                }
            end
        end
    end
end
