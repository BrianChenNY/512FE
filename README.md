# hanlon-jupyter-mysql
hanlon docker + jupyter + mysql

## for fe512 students

Run Jupyter Notebook and MySQL in Docker.  

- Step 01
    - install or upgrade your operating system to latest version
        - for mac, Mojave
        - for windows, Windows 10 Pro (https://stevens.edu/msdnaa).  use your stevens email address to either login (IT confirms you should all have an account) or request an account from both:
            - [the Microsoft/Stevens website](https://e5.onthehub.com/WebStore/Account/VerifyImportedUser.aspx?ws=9a73552b-cf9b-e011-969d-0030487d8897&vsro=8)  
            - [Stevens IT Helpdesk](https://sit.teamdynamix.com/TDClient/Requests/ServiceDet?ID=19685)


- Step 02
    - install docker, https://www.docker.com/products/docker-desktop.  when you install docker make sure to choose **Linux Containers** and not **Windows Containers**
        - for mac, [docker for mac](https://store.docker.com/editions/community/docker-ce-desktop-mac)
        - for windows, [docker for windows](https://store.docker.com/editions/community/docker-ce-desktop-windows)
    - for windows, if you store your file in a different drive location from **C:/**, then you will need to access the docker preferences to add other Shared Folder locations, such as **D:/** or whatever
    - follow the online docker installation instructions carefully and make sure to test the docker installation
    - NOTE: in some cases, you may need to enable virtualization on your computers


- Step 03
    - download the following zip file from Canvas to your computer and unzip:
        - hanlon-jupyter-mysql-fe512.zip
- Step 04
    - place your data files, i.e. csv, txt, and et cetera in the following location:
```
--| hanlon-jupyter-mysql-for-students/
----| mysql/
------| data/
```
- see image below

![00_mysql_data](./.assets/00_mysql_data.png)

- Step 04
    - access a terminal window on your computer.  you may require admin privileges.
        - for mac, Terminal.app
        - for windows, Powershell.  NOTE: do not use PowerShell ISE.
        - enter your terminal switch change directory into the hanlon-jupyter-mysql-for-students/ or whatever your full path to the file may be, for example:
            - cd /home/fe512student/projects/hanlon-jupyter-mysql-for-students/ 


    - ...
```
$ cd hanlon-jupyter-mysql-for-students/
```

- docker starting
```
- to start and run processes
$ docker-compose build

$ docker-compose up
```

- success!  **skip to jupyter notebook access.**
![00_DockerJupyterMySQL_running](./.assets/00_DockerJupyterMySQL_running.png)


- docker stopping.  **NOTE: if everything ran and installed properly you do not need to stop and kill the process.**
```
- to stop and kill processes
$ docker-compose down -v --rmi all --remove-orphans
```

- jupyter notebook access
    - open a browser and enter the url below
```
- http://127.0.0.1:5102/
or
- http://localhost:5102/

```
![00_jupyter](./.assets/00_jupyter.png)

- mysql
    - to enter the mysql container and mysql from the commandline
    - NOTE: you can connect to this MySQL containerized server through MySQL Workbench as normal.  No password is required.
```
$ docker exec -it fe512_mysql /bin/bash

root@05a575ea5b03:/# mysql -h 127.0.0.1 -P 5120 -u root -p
Enter password: [SIMPLY PRESS THE ENTER KEY]

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.12 MySQL Community Server - GPL

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

- to exit mysql and the mysql container

```
mysql> exit
Bye

root@05a575ea5b03:/# exit
exit

```

- Step 05, MySQL Workbench 
    - to connect from MySQL Workbench to MySQL server running in the Docker container
        - create a new connection MySQL connection

- click on **+** sign

![00](./.assets/00_MySQL_Connections.png)


- connection info before

![01](./.assets/01_SetupNewConnection.png)

- connection info after

![02](./.assets/02_StorePasswordForConnection.png)


- test the connection

![03](./.assets/03_TestConnection.png)

- finally click **OK** and click **OK** again
    - start writing your queries
