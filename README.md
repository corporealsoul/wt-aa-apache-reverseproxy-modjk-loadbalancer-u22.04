### Backend Server Configuration,

**Installed Java,**

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo apt install openjdk-19-jre-headless (Tomcat 11 requires latest version of Java)`

`anup@ubuntu-22041-100-REALMREGAL:~$ java -version`

`anup@ubuntu-22041-100-REALMREGAL:~$ update-alternatives --config java`

<br>

### Download Tomcat, https://dlcdn.apache.org/tomcat/

`anup@ubuntu-22041-100-REALMREGAL:~$ wget https://dlcdn.apache.org/tomcat/tomcat-11/v11.0.0-M4/bin/apache-tomcat-11.0.0-M4.tar.gz`

`anup@ubuntu-22041-100-REALMREGAL:~$ ls -ltr`

<br>

### Setup backend-7070,

`anup@ubuntu-22041-100-REALMREGAL:~$ tar -xvzf apache-tomcat-11.0.0-M4.tar.gz `

`anup@ubuntu-22041-100-REALMREGAL:~$ mv apache-tomcat-11.0.0-M4 apache-tomcat-11.0.0-M4-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ ln -sf apache-tomcat-11.0.0-M4-7070 backend-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ cd backend-7070`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ nano conf/server.xml `

    <Server port="7005" shutdown="SHUTDOWN">
    
        <Connector port="7070" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="7443" />

<br>

    <!-- Define an AJP 1.3 Connector on port 7009 -->
    
    <Connector protocol="AJP/1.3"
               address="192.168.56.100"
               port="7009"
               redirectPort="7443"
               secretRequired="false" />

<br>

    <Engine name="Catalina" defaultHost="localhost" jvmRoute="worker1">

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ sudo nano conf/tomcat-users.xml`

    <tomcat-users xmlns="http://tomcat.apache.org/xml"
       <role rolename="admin-gui"/>
       <role rolename="manager-gui"/>
       <user username="admin" password="0tm7s^6IeVs5" roles="admin-gui,manager-gui"/>
    </tomcat-users

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ sudo nano webapps/manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ sudo nano webapps/host-manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ ./bin/shutdown.sh`

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ ./bin/startup.sh`

<br>

### Setup backend-8080,

`anup@ubuntu-22041-100-REALMREGAL:~$ tar -xvzf apache-tomcat-11.0.0-M4.tar.gz `

`anup@ubuntu-22041-100-REALMREGAL:~$ mv apache-tomcat-11.0.0-M4 apache-tomcat-11.0.0-M4-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ ln -sf apache-tomcat-11.0.0-M4-7070 backend-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ cd backend-8080`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ nano conf/server.xml `

    <Server port="8005" shutdown="SHUTDOWN">
    
        <Connector port="8080" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="8443" />

<br>

    <!-- Define an AJP 1.3 Connector on port 8009 -->
    
    <Connector protocol="AJP/1.3"
               address="192.168.56.100"
               port="8009"
               redirectPort="8443"
               secretRequired="false" />

<br>

    <Engine name="Catalina" defaultHost="localhost" jvmRoute="worker2">

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ sudo nano conf/tomcat-users.xml`

    <tomcat-users xmlns="http://tomcat.apache.org/xml"
       <role rolename="admin-gui"/>
       <role rolename="manager-gui"/>
       <user username="admin" password="0tm7s^6IeVs5" roles="admin-gui,manager-gui"/>
    </tomcat-users

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ sudo nano webapps/manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ sudo nano webapps/host-manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ ./bin/shutdown.sh`

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ ./bin/startup.sh`

<br>

### Setup backend-9090,

`anup@ubuntu-22041-100-REALMREGAL:~$ tar -xvzf apache-tomcat-11.0.0-M4.tar.gz `

`anup@ubuntu-22041-100-REALMREGAL:~$ mv apache-tomcat-11.0.0-M4 apache-tomcat-11.0.0-M4-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ ln -sf apache-tomcat-11.0.0-M4-7070 backend-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ cd backend-9090`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ nano conf/server.xml `

    <Server port="9005" shutdown="SHUTDOWN">
    
        <Connector port="9090" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="9443" />

<br>

    <!-- Define an AJP 1.3 Connector on port 9009 -->
    
    <Connector protocol="AJP/1.3"
               address="192.168.56.100"
               port="9009"
               redirectPort="9443"
               secretRequired="false" />

<br>

    <Engine name="Catalina" defaultHost="localhost" jvmRoute="worker3">

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ sudo nano conf/tomcat-users.xml`

    <tomcat-users xmlns="http://tomcat.apache.org/xml"
       <role rolename="admin-gui"/>
       <role rolename="manager-gui"/>
       <user username="admin" password="0tm7s^6IeVs5" roles="admin-gui,manager-gui"/>
    </tomcat-users

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ sudo nano webapps/manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ sudo nano webapps/host-manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ ./bin/shutdown.sh`

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ ./bin/startup.sh`

<br>

### Install Apache and Mod jk.

**Manual installation,**

Install apache is not present then install,

https://tomcat.apache.org/download-connectors.cgi

`anup@ubuntu-22041-100-REALMREGAL:~$ wget https://dlcdn.apache.org/tomcat/tomcat-connectors/jk/tomcat-connectors-1.2.48-src.tar.gz`

`anup@ubuntu-22041-100-REALMREGAL:~$ tar -xvzf tomcat-connectors-1.2.48-src.tar.gz `

`anup@ubuntu-22041-100-REALMREGAL:~$ cd tomcat-connectors-1.2.48-src/`


**APT Installation,**

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo apt-get install libapache2-mod-jk`

<br>

### Enable JK Module,

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl restart apache2.service`

`anup@ubuntu-22041-100-REALMREGAL:~$ apache2ctl -M | grep jk`

`anup@ubuntu-22041-100-REALMREGAL:~$ netstat -tulpn`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ ls -ltr /etc/apache2/mods-enabled/`

`anup@ubuntu-22041-100-REALMREGAL:~$ ls -ltr /usr/lib/apache2/modules/`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/mods-available/jk.load`

    LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/workers.properties`

    ### configure jk-status
    worker.list=jk-status
    worker.jk-status.type=status
    worker.jk-status.read_only=true
    
    ### configure jk-manager
    worker.list=jk-manager
    worker.jk-manager.type=status
    
    ### configure LOADBALANCER
    worker.list=jkstatus, lb_router
    worker.lb_router.type=lb
    worker.lb_router.balance_workers=worker1,worker2,worker3
    worker.lb_router.sticky_session=1
    
    ### Set Worker
    worker.worker1.port=7009
    worker.worker1.host=192.168.56.100
    worker.worker1.type=ajp13
    worker.worker1.lbfactor=2
    worker.worker1.connection_pool_timeout=600
    worker.worker1.socket_keepalive=1
    
    worker.worker2.port=8009
    worker.worker2.host=192.168.56.100
    worker.worker2.type=ajp13
    worker.worker2.lbfactor=2
    worker.worker2.connection_pool_timeout=600
    worker.worker2.socket_keepalive=1
    
    worker.worker2.port=9009
    worker.worker2.host=192.168.56.100
    worker.worker2.type=ajp13
    worker.worker2.lbfactor=2
    worker.worker2.connection_pool_timeout=600
    worker.worker2.socket_keepalive=1

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ grep -r JkWorkersFile /etc/apache2`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/mods-available/mod_jk.conf`

    ServerName 192.168.56.100
    
    LoadModule jk_module "/usr/lib/apache2/modules/mod_jk.so"
    
    JkWorkersFile /etc/apache2/workers.properties
    JkLogFile /var/log/apache2/mod_jk.log
    
    #JkMount /myapp/* lb_router
    #JkMount /* lb_router
    JkMount /docs/*  lb_router
    JkMount /docs*  lb_router
    JkMount /docs/*  jk-status
    JkMount /docs*  jk-status
    JkMount /docs/*  jk-manager
    JkMount /docs*  jk-manager
    
    
    JkLogLevel debug
    
    JkLogStampFormat "[%a %b %d %H:%M:%S %Y]"
    JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories
    JkRequestLogFormat "%w %V %T"

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/mods-available/jk.conf`

    <IfModule jk_module>
        JkWorkersFile /etc/apache2/workers.properties
    </IfModule>

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/sites-enabled/000-default.conf`

    <VirtualHost *:80>
            ServerName 192.168.56.100
            JkMount /docs/*  lb_router
            JkMount /docs*  lb_router
            JkMount /docs/*  jk-status
            JkMount /docs*  jk-status
            JkMount /docs/*  jk-manager
            JkMount /docs*  jk-manager
    </VirtualHost>

`anup@ubuntu-22041-100-REALMREGAL:~$ apachectl configtest`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl restart apache2.service`

### On your favorite browser : http://192.168.56.100/docs/

<br>
