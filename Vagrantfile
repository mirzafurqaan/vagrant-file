$script = <<-SCRIPT

echo "cd /vagrant" >> /home/vagrant/.profile
echo "All good!!"
SCRIPT

Vagrant.configure("2") do |config|

    # hyperv (Windows 10 Pro)  and   VirtualBox (Windows 10 Home)
    # Ubuntu 64 bit
    config.vm.box = "bento/ubuntu-16.04"


    config.ssh.username = 'vagrant'
    config.ssh.password = 'vagrant'
    config.ssh.insert_key = 'true'


    # Ports foward
    # For SSH
   # config.vm.network "forwarded_port", guest: 2222, host: 2222
    # For playground
    config.vm.network "forwarded_port", guest: 8080, host: 8080
    # For REST Server
    config.vm.network "forwarded_port", guest: 3000, host: 3000
    # For Docker Deamon
    config.vm.network "forwarded_port", guest: 2375, host: 2375
    # For Orderer Container
    config.vm.network "forwarded_port", guest: 7050, host: 7050
    # For Peer Container
    config.vm.network "forwarded_port", guest: 7051, host: 7051
    # For Peer Container
    config.vm.network "forwarded_port", guest: 7052,
     host: 7052
    # For Peer Container
    config.vm.network "forwarded_port", guest: 7053, host: 7053
    # For CA Container
    config.vm.network "forwarded_port", guest: 7054, host: 7054
    # For CouchDB Container
    config.vm.network "forwarded_port", guest: 5984, host: 5984

    # Zookeeper
    #config.vm.network "forwarded_port", guest: 2181, host: 2181

    # For Kafka Broker
    #config.vm.network "forwarded_port", guest: 9092, host: 9092

    # For Kafka Manager
    config.vm.network "forwarded_port", guest: 9000, host: 9000


    # This gets executed for both vm1 & vm2
    # config.vm.provision "shell", inline:  "echo 'All good'"
    config.vm.provision "shell", inline:  $script
  
    # To use a diffrent Hypervisor create a section config.vm.provider
    # And comment out the following section
    # Configuration for Virtual Box
    config.vm.provider :virtualbox do |vb|
      # Change the memory here if needed - 2 Gb memory on Virtual Box VM
      vb.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "1"]
      # Change this only if you need destop for Ubuntu - you will need more memory
      vb.gui = false
      # In case you have DNS issues
      # vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

    # Configuration for Windows Hyperv
    config.vm.provider :hyperv do |hv|
      # Change the memory here if needed - 2 Gb memory on Virtual Box VM
      hv.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "1"]
      # Change this only if you need destop for Ubuntu - you will need more memory
      hv.gui = false
      # In case you have DNS issues
      # vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end


  end