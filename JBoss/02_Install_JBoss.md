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

### **Cấu hình Export display**
- Do bộ cài đặt **Oracle Weblogic** cần cài đặt qua giao diện, vì vậy cần export display để tận dụng màn hình giao diện của host thực hiện SSH vào server. Thực hiện 2 lệnh sau :
    ```
    # yum install xhost xorg-x11-* -y
    # xhost +
    access control disabled, clients can connect from any host
    # export DISPLAY=192.168.5.1:0.0
    ```
> Trong đó : `192.168.5.1` là IP của localhost.
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
    # java -jar jboss-eap-7.4.0-installer.jar
    ```
- **B6 :** Chọn ngôn ngữ cài đặt -> ***OK*** : 

    <p align=center><img src=https://i.imgur.com/6GR9C54.png></p>

- **B7 :**

    <p align=center><img src=https://i.imgur.com/q1cpfqb.png></p>

- **B8 :**

    <p align=center><img src=https://i.imgur.com/Sk3rS20.png></p>

- **B9 :**

    <p align=center><img src=https://i.imgur.com/duXqtB6.png></p>

- **B10 :**

    <p align=center><img src=https://i.imgur.com/KtODqHH.png></p>

- **B11 :**

    <p align=center><img src=https://i.imgur.com/DvvUlzf.png></p>

- **B12 :**

    <p align=center><img src=https://i.imgur.com/K1fxKHl.png></p>

- **B13 :**

    <p align=center><img src=https://i.imgur.com/b6wGF2p.png></p>

- **B14 :**

    <p align=center><img src=https://i.imgur.com/uTQZ0om.png></p>

- **B15 :**

    <p align=center><img src=https://i.imgur.com/3G1Jvgh.png></p>

### **Cấu hình JBoss EAP run as a service**