# sistemas operativos entrega 2

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"

  # --------------- VM #1: web (Nginx) ---------------
  config.vm.define "web" do |web|
    web.vm.hostname = "web"
    web.vm.network "forwarded_port", guest: 80, host: 8080
    web.vm.provider "virtualbox" do |vb|
      vb.name = "so-webb"
      vb.memory = 1024
      vb.cpus = 1
    end

    web.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible-web/playbook_web.yml"
      ansible.inventory_path = "ansible-web/inventory.ini"
      ansible.become = true
    end
  end

  # --------------- VM #2: monitor (Prometheus + Grafana) ---------------
  config.vm.define "monitor" do |mon|
    mon.vm.hostname = "monitor"
    mon.vm.network "forwarded_port", guest: 3000, host: 3000   # Grafana
    mon.vm.network "forwarded_port", guest: 9090, host: 9090   # Prometheus
    mon.vm.provider "virtualbox" do |vb|
      vb.name = "so-monitorr"
      vb.memory = 2048
      vb.cpus = 2
    end

    mon.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible-monitor/playbook_monitor.yml"
      ansible.inventory_path = "ansible-monitor/inventory.ini"
      ansible.become = true
    end
  end
end
