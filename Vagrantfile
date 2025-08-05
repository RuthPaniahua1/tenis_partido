Vagrant.configure("2") do |config|
  config.vm.provider "docker" do |d|
    d.image = "tenis-ansible-image"
    d.name = "ansible_docker"
    d.ports = ["2222:22"]
    d.cmd = ["bash", "-c", <<-SCRIPT
      cd /vagrant &&
      echo "Ejecutando playbook..." &&
      ansible-playbook -i hosts.ini playbook.yml &&
      echo "Contenido generado de partido.txt:" &&
      cat /vagrant/partido.txt &&
      tail -f /dev/null
    SCRIPT
    ]
  end

  config.vm.synced_folder ".", "/vagrant"
end
