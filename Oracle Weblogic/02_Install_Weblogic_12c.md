# Install Weblogic 12c on RedHat 7
### **Cài đặt Oracle Java Development Kit (JDK) 8**
- **B1 :** Download **JDK 8** tại [link](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html) :

    <img src=https://i.imgur.com/q8asx96.png>

- **B2 :** Copy file `jdk-8u202-linux-x64.rpm` vào server Linux cần cài đặt, sau đó cài đặt sử dụng `rpm` :
    ```
    # rpm -ivh jdk-8u202-linux-x64.rpm
    ```
    <img src=https://i.imgur.com/pjPBd7U.png>

- **B3 :** Set biến môi trường `JAVA_HOME` :
    ```
    # echo "export JAVA_HOME=/usr/java/jdk1.8.0_202-amd64" >> /etc/profile
    ```
- **B4 :** Kiểm tra phiên bản **Java** vừa cài đặt :
    ```
    # java -version
    ```
    <img src=https://i.imgur.com/Wxncb7a.png>

### **Cài đặt Oracle Weblogic Server 12c**
- **B1 :** Download bộ cài của **Oracle WebLogic Server 12c** tại [link](https://www.oracle.com/middleware/technologies/weblogic-server-installers-downloads.html) :

    <img src=https://i.imgur.com/Gcnm59y.png>

- **B2 :** Copy file `fmw_12.2.1.4.0_wls_lite_Disk1_1of1.zip` vào server Linux cần cài đặt.
- **B3 :** Tạo user `oracle` và group `oinstall` để quản lý và cài đặt **Oracle Weblogic Server 12c** :
    ```
    # groupadd -g 1001 oinstall
    # useradd -u 1001 -g oinstall oracle
    # passwd oracle
    ```
- **B4 :** Tạo một số thư mục cần thiết cho **Oracle Weblogic Server 12c** :
    ```
    # mkdir -p /u01/app/oracle/product/12.2.1
    # mkdir -p /u01/app/oracle/config/{domains,applications}
    # chown -R oracle:oinstall /u01/app
    # chmod -R 775 /u01
    ```
- **B5 :** Chuyển qua user `oracle` :
    ```
    # su - oracle
    ```
- **B6 :** Export biến môi trường :
    ```
    $ export ORACLE_BASE=/u01/app/oracle
    $ export ORACLE_HOME=$ORACLE_BASE/product/12.2.1
    $ export MW_HOME=$ORACLE_HOME
    $ export WLS_HOME=$MW_HOME/wlserver
    $ export DOMAIN_BASE=$ORACLE_BASE/config/domains
    $ export DOMAIN_HOME=$DOMAIN_BASE/mydomain
    ```
- **B7 :** Unzip file `fmw_12.2.1.4.0_wls_lite_Disk1_1of1.zip` :
    ```
    $ cd /opt
    $ unzip fmw_12.2.1.4.0_wls_lite_Disk1_1of1.zip
    ```
    <img src=https://i.imgur.com/Ji9jkPY.png>

- **B8 :** Chạy file `fmw_12.2.1.4.0_wls_lite_generic.jar` vừa được giải nén :
    ```
    $ java -jar fmw_12.2.1.4.0_wls_lite_generic.jar
    ```