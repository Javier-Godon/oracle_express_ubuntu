# Deployment of oracle express on Ubuntu 22.04

Oracle does not include any option to install Oracle XE directly in Debian distributions
<https://www.oracle.com/se/database/technologies/appdev/xe/quickstart.html>

If you search in google you wil probably find some "solutions" parsing .rpm packages into .dev ...good luck!!

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/29df07ae-d746-43e2-9ad2-24ebe6b6ae0f)

We are going to install it using docker which will work in any case.

If you don´t have Docker installed and you are not an expert, I recommend you to install Docker desktop for ubuntu following the next instructions:  

<https://docs.docker.com/desktop/install/ubuntu/>  

<https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository>  

In my case, I have dowloaded version 4.24.0 and I have it in downloads

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/20ab5091-06b9-4887-95cf-ce486984edf0)

If you open a terminal in that location then you can execute:  

```
$ sudo apt-get update
$ sudo apt-get install ./docker-desktop-4.24.0-amd.deb
```

Once Docker desktop is installed open it and then following Oracle instructions we should go to it's registry and download the image that we need,
in my case Oracle Express 21.3.0  

<https://container-registry.oracle.com> 

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/2df10174-77a7-424a-ab21-d03c761d60c0)

then go to database

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/4ee84383-421d-43f3-8da7-d5c34b9b64e3)

and choose express

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/45a1b4c5-c54e-4d78-8c13-046dffab1341)

then open a terminal and execute the pull command (Latest or the version that you want. Is a good practice to chose a version)
In my case the last version is 21.3.0

```
$ docker pull container-registry.oracle.com/database/express:21.3.0-xe
```

Now your Docker Desktop shoul show the image that you have already downloaded

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/a5e140c7-8dc4-49a5-9f82-8b1aa43ec903)

Using the image that we have already downloaded we are going to run a container using docker compose
Create a folder (in my case I will call it oracle-express) and inside that folder a document .yaml and call it docker-compose.yaml
fill in the document as follows (use the name of your image, in my case is: container-registry.oracle.com/database/express:21.3.0-xe)
and create another folder (I will call it oracle-express too), so I will have a folder called oracle-express and inside another folder called
oracle-express and a document called docker-compose.yaml


![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/7a6fc983-cf42-48e0-972f-a49ec49e575e)

then open a terminal inside of that folder (the one that contains the docker compose and the second folder) and execute

```
$ sudo chmod -R o+w oracle-express

```

and then

```
$ docker compose up
```
or maybe you need to use
```
$ docker-compose up
```

<https://docs.docker.com/engine/reference/commandline/compose_up/>  

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/d4560a70-a885-4fcf-a0fe-a76f8f41873f)

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/a49c63c2-418a-4cb8-8f41-f882f3b278b3)


Now your database is up and running.

You can start and stop your database from your docker desktop, playing or stoping your container.

some reading:

<https://docs.docker.com/desktop/use-desktop/>

Now you can connect to the database using a client

## Connection using DBeaver

Use the password and port specified on your docker-compose.yaml, in my case: 
```txt
password: oracle
port: 1521
```

![image](https://github.com/Javier-Godon/oracle_express_ubuntu/assets/32432254/a2609bc8-6c80-450e-953a-02f583c8609f)




Enjoy!! :)












