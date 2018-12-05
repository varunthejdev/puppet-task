"# puppet-task" 
# execute apt update

exec {"apt update":
path => ['usr/bin'],
}

# install apache2 package

package {"apache2":
ensure => installed,
}

# start service apache2

service {"apache2":
ensure => started,
}

# install mysql-server package

package {"mysql":
ensure => installed,
}

# start mysql service

service {"mysql":
ensure => started,
}

# install php package

package {"php":
ensure => installed,
}

# install php-mysql package

package {"php-mysql":
ensure => installed,
}

# install libapache2-mod-php package

package {"libapache2-mod-php":
ensure => installed,
}

# install php-mcrypt package

package {"php-mycrypt":
ensure => installed,
}

# install php-gd package

package {"php-gd":
ensure => installed,
}

# install libssh2-php package

package {"libssh2-php":
ensure => installed,
}

# Create file /tmp/mysqlcommands based on a source file /var/mysqlcommands

file {"/tmp/mysqlcommands":
ensure => present,
source => /var/mysqlcommands,
}


# mysql -uroot -p123@India < /tmp/mysqlcommands && touch /var/flagmysqlcommands

exec { "mysql -uroot -p123@India < /tmp/mysqlcommands && touch /var/flagmysqlcommands>":
  creates => '/var/flagmysqlcommands',
  path    => ['/usr/bin'],
}

# run below command through exec and use creates parameter
#"mysqladmin -u root password 123@India && touch /var/flagmysqlroot"

exec { "mysqladmin -u root password 123@India && touch /var/flagmysqlroot":
  creates => '/var/flagmysqlroot',
  path    => ['/usr/bin'],
}

# Extract wordpress with "tar xzvf latest.tar.gz"

exec { 'tar xzvf latest.tar.gz':
ensure => present,
}

# copy files to apache with "cp -R /root/puppetcodes/wordpress/* /var/www/html/"

exec {"cp -R /root/puppetcodes/wordpress/* /var/www/html/":
ensure => present,
source => '/root/puppetcodes/wordpress',
}

#Create file /var/www/html/wp-config.php by copying /var/wp-config-sample.php

file {"/var/www/html/wp-config.php":
ensure => present,
source => '/var/wp-config-sample.php',
}

#Run the below command and make use of creates paramter
#mkdir /var/www/html/wp-content/uploads && touch /var/flagmkdir

exec {"mkdir /var/www/html/wp-content/uploads && touch /var/flagmkdir":
ensure => present,
creats => '/var/flagmkdir',
}

# chown -R :www-data /var/www/html/wp-content/uploads


# delete file /var/www/html/index.html

file {"/var/www/html/index.html":
ensure => deleted,
}



















