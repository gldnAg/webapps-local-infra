Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  #Docker構成変更時は、forwarded_port設定を適宜変更する
  config.vm.network "forwarded_port", guest: 8001, host: 8001, id: "Rancher"
  config.vm.network "forwarded_port", guest: 8010, host: 8010, id: "phpLDAPadmin"
  config.vm.network "forwarded_port", guest: 3000, host: 3000, id: "Rocket.chat"

  #メモリとCPUの割り当てはホストマシンのリソースに合わせて調整する
  config.vm.provider "virtualbox" do |vb|
    vb.name = "vagrant-ubuntu"
    vb.memory = 4096
    vb.cpus = 2
    vb.customize [
      "modifyvm", :id,
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--paravirtprovider", "kvm",
    ]
  end
end