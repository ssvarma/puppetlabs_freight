Freight Module
===
  Installs and configures a local APT repo using freight   

Requires:
---
  The apache class and vhost definition

Actions:
---
  Install appropriate apache vhost for freight instance  
  Add rcrowley's repository key so freight can be apt-installed  
  Install, configure and setup freight instance  
  Installs gpg-agent for signing packages  

Defined Type: 
---
   Creates a configuration file for freight, creates a vhost, and builds out directories for freight

	freight::repo
   
Sample Usage:
---
	freight::repo { 'freight':
	freight_vhost_name  => 'freight.somewhere.com',
	freight_docroot     => '/var/www/html',
	freight_gpgkey      => 'me@somewhere.com',
	freight_libdir      => '/var/lib/freight',
	}
 
Parameters:
---
-  The $freight_vhost_name choses a virtual host name for the repo  
-  The $freight_docroot chooses a docroot to serve the repo out of
   (used for the vhost and for freight config)  
-  The $freight_gpgkey is the gpg key used to sign the repository  
-  The $freight_group is used to define the group for the docroot and libdir  
-  The $freight_libdir is where the freight stores the debs, before
   hard-linking them into the vhost docroot  

