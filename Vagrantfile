Vagrant.configure("2") do |config|
  config.vm.define "ansible_docker" do |ansible|
    ansible.vm.provider "docker" do |d|
      d.image = "tenis-ansible-image"
      d.has_ssh = true
      d.name = "ansible_docker"
      d.cmd = ["/usr/sbin/sshd", "-D"]
      d.ports = ["2222:22"]
      d.volumes = ["F:/tenis_partido_vagrant_docker/tenis_partido:/vagrant"]
    end

    ansible.vm.synced_folder ".", "/vagrant"
    ansible.vm.boot_timeout = 600

    ansible.ssh.username = "vagrant"
    ansible.ssh.password = "vagrant"
    ansible.ssh.insert_key = false

    ansible.vm.provision "shell", inline: <<-SHELL
      cd /vagrant
      ansible-playbook -i hosts.ini playbook.yml
      echo "Contenido generado de partido.txt:"
      cat /vagrant/partido.txt
    SHELL
  end
end
