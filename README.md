Description
=============
A simple blog powered by Flask, MongoDB, MongoEngine, Gunicorn, Supervisor, Nginx and Windows Azure.

Usage
-------------
* conf/gunicorn.conf

    workers = numbers_of_your_cpus
    
    bind = 'unix:/yourpath/tumblog.sock'
  

* conf/tumblelog.conf

    command=/yourpath/gunicorn manage:app -c /yourpath/gunicorn.conf
    
    directory=/yourpath/tumblelog
  
    stdout_logfile=/yourpath/gunicorn_supervisor.log
  

* conf/tumblelog_nginx.conf
  
    server unix:/yourpath/tumblog.sock;
  
    access_log /yourpath/nginx-access.log;
    
    error_log /yourpath/nginx-error.log;
  
    location /media {alias /yourpath/media;}
    
    location /static {alias /yourpath/static;}