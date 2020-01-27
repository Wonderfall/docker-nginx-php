Base image for wonderfall/nextcloud.

## BUILD IMAGE
### Build arguments
* BUILD_CORES : Number of cpu's core for compile (default : empty for use all cores)
* NGINX_VER : Nginx version (default : latest version)
* NGINX_GPG : Nginx gpg fingerprint
* NGINX_CONF : Nginx build arguments (default : see Dockerfile)
* PHP_VER : PHP version (default : latest version)
* PHP_MIRROR: Mirror for download PHP (default : http://fr2.php.net)
* PHP_GPG : PHP gpg fingerprint
* PHP_CONF : PHP build arguments (default : see Dockerfile)
* PHP_EXT_LIST : PHP extensions list, for install there (default : see Dockerfile)
* CUSTOM_BUILD_PKGS : Necessary packages for build PHP extension, there packages are remove after build (default : see Dockerfile)
* CUSTOM_PKGS : Necessary package for PHP extension (default : see Dockerfile)

## Configuration
### Environments
* UID : Choose uid for launch rtorrent (default : 991)
* GID : Choose gid for launch rtorrent (default : 991)

### Volumes
* /nginx/sites-enabled : Place your vhost here
* /nginx/log : Log emplacement
* /nginx/run : Here is pid and lock file
* /nginx/conf/nginx.conf : General configuration of nginx
* /nginx/conf.d : folder for other configuration (ex : php.conf, headers_param.conf)

if you mount /nginx/conf.d, use this php.conf :
```shell
location ~ \.php$ {
    fastcgi_index index.php;
    fastcgi_pass unix:/php/run/php-fpm.sock;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    include /nginx/conf/fastcgi_params;
}
```

### Ports
* 8080
