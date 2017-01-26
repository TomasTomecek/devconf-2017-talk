Vagrant.configure(2) do |config|
  config.vm.provider "libvirt" do |libvirt, override|
    libvirt.driver = "kvm"
    libvirt.memory = 2048
    libvirt.cpus = 1
    libvirt.cpu_mode = 'host-passthrough'  # Host CPU does not provide required features: svm
  end

  config.vm.define :worst_builder do |vagrant_host|
    # Box name
    # vagrant_host.vm.box = "projectatomic/adb"
    vagrant_host.vm.box = "fedora/25-cloud-base"
    vagrant_host.vm.hostname = "worst"
    
    config.vm.synced_folder "./", "/home/vagrant/sync/", type: "rsync",
                            rsync__exclude: [ ".git/", ".#*", "*~" ] #want to get all files, but if you target the root, vagrant uses --delete which is no fun
  end

end

