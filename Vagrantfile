VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = '~/.ssh/id_rsa'
    override.vm.box               = 'digital_ocean'
    override.vm.box               = 'AndrewDryga/digital-ocean'
    provider.token                = ENV['DIGITALOCEAN_ACCESS_TOKEN']
    provider.image                = 'Ubuntu 14.04 x64'
    provider.region               = 'sgp1'
    provider.size                 = '512MB'

    if ENV['WERCKER'] == 'true'
      provider.ssh_key_name = 'wercker-example'
    else
      provider.ssh_key_name = 'My MacBook Air'
    end
  end

  config.vm.provision :shell, inline: <<-EOF
    sudo apt-get install -y nginx
  EOF
end
