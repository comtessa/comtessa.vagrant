# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/xenial64"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  # Mneme - Muse des Gedächtnis
  # Server für SCM-Tools
  config.vm.define "mneme.informatik.unibw-muenchen.de", primary: true do |mneme|
    mneme.vm.provider "virtualbox" do |vb|
      vb.name = "mneme"
      vb.memory = 8192
      vb.cpus = 8
      vb.customize ["modifyvm", :id,
                    "--cpuexecutioncap", "50",
                    "--groups", "/Vagrant/Comtessa"
                   ]
    end
    mneme.vm.network :private_network, ip: "192.168.1.200"

    config.vm.provision "ansible" do |ansible|
      ansible.verbose = ""
      ansible.playbook = "comtessa.ansible.playbooks/mneme.yml"
    end
  end

  # Klio - Muse der Geschichtsschreibung
  # Server für Monitoring
  # * OMD
  # * Sentry
  # * Logstash
  config.vm.define "klio.informatik.unibw-muenchen.de", autostart: false do |klio|
    klio.vm.provider "virtualbox" do |vb|
      vb.name = "klio"
      vb.memory = 8192
      vb.cpus = 8
      vb.customize ["modifyvm", :id,
                    "--cpuexecutioncap", "50",
                    "--groups", "/Vagrant/Comtessa"
                   ]
    end
    klio.vm.network :private_network, ip: "192.168.1.201"

    config.vm.provision "ansible" do |ansible|
      ansible.verbose = ""
      ansible.playbook = "comtessa.ansible.playbooks/klio.yml"
    end
  end


#  # Melete - Muse der Übung/Fertigkeit
#  # Server für
#  config.vm.define "melete.informatik.unibw-muenchen.de", autostart: false do |melete|
#    melete.vm.provider "virtualbox" do |vb|
#      vb.name = "melete"
#      vb.memory = 8192
#      vb.cpus = 8
#      vb.customize ["modifyvm", :id,
#                    "--cpuexecutioncap", "50",
#                    "--groups", "/Vagrant/Comtessa"
#                   ]
#    end
#    melete.vm.network :private_network, ip: "192.168.1.202"
#
#    config.vm.provision "ansible" do |ansible|
#      ansible.verbose = ""
#      ansible.playbook = "melete.yml"
#    end
#  end

end
