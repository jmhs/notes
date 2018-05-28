# Nginx Notes


## Performance
- Nginx does not use any server-side programming language unlike Apache, allowing it to have better(lower resource consumption) and more predictable memory performance.
- Event-drivent , asynchronous architecture, doesn't rely on threads to handle requests
- Made to handle 10k concurrent connections - C10K problem
- Nginx interprets incoming requests as URI locations, whereas Apache prefers interpret it as filesystem locations.
- CentOS - Nginx package doesnt come with Yum as std, `yum install epel-release`

## Nginx fundamentals tutorial

### Installation
```
sudo apt-get install nginx
sudo apt-get upgrade
sudo apt-get install build-essential //compilation tools suce as make
wget http://nginx.org/download/nginx-1.11.3.tar.gz // download source (mainline release)
```
- extract tarball, navigate into dir
- z means (un)z̲ip.
x means ex̲tract files from the archive.
v means print the filenames v̲erbosely.
f means the following argument is a f̱ilename.

```
tar -zxvf nginx-1.11.3.tar.gz
```

```
cd nginx-1.11.3/
```

Install dependencies, libpcre3 for regex, libssl for ssl certs, zlib for compressing static resources
```
apt-get install libpcre3 libpcre3-dev libpcrecpp0 libssl-dev zlib1g-dev
```

params after ./configure to add installation specific/modules before compile i.e. ggle compile-time options for more
1. set path for nginx executable; do it here instead of moving it afterwards
2. set name of conf file, etc/enginx/ most common place
3. set log config --with-debug for well, more details
4. modules! pcre for regex in config files and http_ssl for ssl!

```
 ./configure
   --sbin-path=/usr/bin/nginx    
   --conf-path=/etc/nginx/nginx.conf
   --error-log-path=/var/log/nginx/error.log
   --http-log-path=/var/log/nginx/access.log
   --with-debug
   --with-pcre
   --with-http_ssl_module
```
### Adding Nginx as a Service & Updating custom build
