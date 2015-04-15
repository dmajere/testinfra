# vim: ts=2 sw=2 et ft=ruby

Vagrant.configure("2") do |config|
  config.ssh.username = "root"
  config.vm.define "debian" do |debian|
    debian.vm.provider "docker" do |docker|
      docker.build_dir = "images/debian"
      docker.has_ssh = true
    end
  end

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.provider "docker" do |docker|
      docker.build_dir = "images/ubuntu"
      docker.has_ssh = true
    end
  end

  config.vm.define "centos" do |centos|
    centos.vm.provider "docker" do |docker|
      docker.build_dir = "images/centos"
      docker.has_ssh = true
    end
  end
end
