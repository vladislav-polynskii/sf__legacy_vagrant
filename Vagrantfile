Vagrant.configure("2") do |config|
  config.vm.define "postgresql" do |postgresql|
     postgresql.vm.box = "ubuntu/bionic64"
     postgresql.vm.network "forwarded_port", guest: 5432, host: 5432, host_ip: "127.0.0.1", auto_correct: true
     postgresql.vm.provision "shell", inline: <<-SHELL
         apt-get update
         apt-get install wget ca-certificates -y
	     wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
	     sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
	     apt-get update
	     DEBIAN_FRONTEND=noninteractive apt-get install postgresql-8.4 -y
		 /etc/init.d/postgresql start
		 /etc/init.d/postgresql status
    SHELL
   end
end
