# Install JBoss trên Redhat 7
> ## **Prequisites**
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

### **Download JBoss EAP Installer**
- **B1 :** Truy cập [**Red Hat Customer Portal**](https://access.redhat.com/), chọn **Downloads** :

    <img src=https://i.imgur.com/0hFjpYU.png>

- **B2 :** Chọn **Red Hat JBoss Enterprise Application Platform** :

    <img src=https://i.imgur.com/q9LaxFw.png>

- **B3 :** 

    <img src=https://i.imgur.com/neWwDtq.png>

- **B4 :** Copy bộ cài vào server cần cài đặt.
- **B5 :** Chạy bộ cài :
    ```
    # java -jar jboss-eap-7.4.0-installer.jar -console
    ```
- **B6 :** Chọn `0` :

    <p align=center><img src=https://i.imgur.com/IPFmJJJ.png></p>

- **B7 :** Chọn `1` :

    <p align=center><img src=https://i.imgur.com/UYUie9V.png></p>

- **B8 :**

    <p align=center><img src=https://i.imgur.com/7nE5FXC.png></p>

- **B9 :**

    <p align=center><img src=https://i.imgur.com/u4GR1gD.png></p>

    <p align=center><img src=https://i.imgur.com/U4ckQrt.png></p>

- **B10 :**

    <p align=center><img src=https://i.imgur.com/7h1D1XR.png></p>

- **B11 :**

    <p align=center><img src=https://i.imgur.com/mLEok3X.png></p>

- **B12 :**

    <p align=center><img src=https://i.imgur.com/qRq4O1M.png></p>

- **B13 :**
    ```
    # subscription-manager repos --enable=jb-eap-7-for-rhel-RHEL_VERSION-server-rpms
    ```
### **Cấu hình EAP run as a service**
- **B1 :** Chỉnh sửa `JBOSS_HOME` và `JBOSS_USER` trong file cấu hình `/root/EAP-7.4.0/bin/init.d/jboss-eap.conf` :
    ```conf
    ...
    ## Location of JBoss EAP
    JBOSS_HOME="/root/EAP-7.4.0"

    ## The username who should own the process.
    JBOSS_USER=root
    ...
    ```
- **B2 :** Copy file cấu hình `jboss-eap.conf` vừa chỉnh sửa vào thư mục `/etc/default` :
    ```
    # sudo cp /root/EAP-7.4.0/bin/init.d/jboss-eap.conf /etc/default
    ```
- **B3 :** Copy startup script cho service `jboss-eap-rhel` vào thư mục `/etc/init.d` :
    ```
    # sudo cp /root/EAP-7.4.0/bin/init.d/jboss-eap-rhel.sh /etc/init.d
    # sudo chmod +x /etc/init.d/jboss-eap-rhel.sh
    ```
- **B4 :** Khởi động dịch vụ `jboss-eap-rhel` :
    ```
    # sudo service jboss-eap-rhel start
    ```
