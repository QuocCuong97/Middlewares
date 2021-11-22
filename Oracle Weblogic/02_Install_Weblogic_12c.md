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

### **Cấu hình Export display**
- Do bộ cài đặt **Oracle Weblogic** cần cài đặt qua giao diện, vì vậy cần export display để tận dụng màn hình giao diện của host thực hiện SSH vào server. Thực hiện 2 lệnh sau :
    ```
    # yum install xhost xorg-x11-* -y
    # xhost +
    access control disabled, clients can connect from any host
    ```
> ***Chú ý :*** Nên sử dụng công cụ **MobaXterm**, hoặc **PuTTY** để thực hiện SSH.
### **Cài đặt Oracle Weblogic Server 12c**
- **B1 :** Download bộ cài của **Oracle WebLogic Server 12c** tại [link](https://www.oracle.com/middleware/technologies/weblogic-server-installers-downloads.html) :

    <img src=https://i.imgur.com/Gcnm59y.png>

- **B2 :** Copy file `fmw_12.2.1.4.0_wls_lite_Disk1_1of1.zip` vào thư mục `/opt` trên server Linux cần cài đặt.
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
    $ export DISPLAY=192.168.5.1:0.0
    ```
    > Trong đó : `192.168.5.1` là IP của localhost.
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
    <img src=https://i.imgur.com/rKmcxVs.png>

- **B9 :** Chọn location cho **Oracle Inventory directory** và **OS group** cho **Weblogic Server** -> ***OK***:

    <p align=center><img src=https://i.imgur.com/jZr5Tsu.png width=60%></p>

- **B10 :** Tại cửa sổ **Welcome**, chọn ***Next*** :

    <p align=center><img src=https://i.imgur.com/dbyLf21.png width=60%></p>

- **B11 :** Tại cửa sổ **Auto Updates**, chọn ***Skip Auto Updates*** để bỏ qua chế độ tự động update, sau đó chọn ***Next*** để tiếp tục :

    <p align=center><img src=https://i.imgur.com/RL8bHGu.png width=60%></p>

- **B12 :** Tại cửa sổ **Installation Location**, chọn thư mục Oracle Home -> ***Next*** :

    <p align=center><img src=https://i.imgur.com/Q9z0a47.png width=60%></p>

- **B13 :** Tại cửa sổ **Installation Type**, chọn ***Weblogic Server*** -> ***Next*** :

    <p align=center><img src=https://i.imgur.com/bosJOu0.png width=60%></p>

- **B14 :** Tại cửa sổ **Prequisite Checks**, chọn ***Next*** để tiếp tục :

    <p align=center><img src=https://i.imgur.com/MjdER5a.png width=60%></p>

- **B15 :** Tại cửa sổ **Installation Summary**, chọn ***Install*** để bắt đầu cài đặt :

    <p align=center><img src=https://i.imgur.com/IohNTlO.png width=60%></p>

- **B16 :** Quá trình cài đặt diễn ra, sau khi hoàn tất, chọn ***Next*** -> ***Finish*** để kết thúc quá trình cài đặt :

    <p align=center><img src=https://i.imgur.com/KYaMghc.png width=60%></p>

    <p align=center><img src=https://i.imgur.com/ZygiGml.png width=60%></p>

    <p align=center><img src=https://i.imgur.com/q70kc9r.png width=60%></p>

### **Cấu hình Oracle Weblogic Server 12c**

https://www.centlinux.com/2018/12/install-oracle-weblogic-12c-server-on-centos-7.html