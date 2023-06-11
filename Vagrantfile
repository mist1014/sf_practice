Vagrant.configure("2") do |config|
config.vm.box = "generic/ubuntu1804"
config.vm.provision "file", source: "~/projects/vagrant2/test", destination: "~/test"
config.vm.provision "shell", inline: <<-SHELL
    echo "Updating system"

    sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

    apt-get update



    echo "Installing postgres"
    apt-get install -y postgresql postgresql-client python3 python3-pip libpq-dev && python3 -m pip install psycopg2 Django

 SHELL
end

