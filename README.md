# mule-docker-demo
This project is to dockerize the mule application 

# Sample application 
demo-mule application zip file is checked into the repository. 
This is basic application which prints the log "Inside the container and Application demo-mule" and returns the response "Response from the container and Application demo-mule"

# Steps to package an application.
1. Select **Export** from the File menu.
2. In the **Import** wizard, click to expand the Mule folder, and select Anypoint Studio Project to Mule Deployable Archive (includes Studio metadata), then click Next.
3. **Select the project** that you want to export, and click **Next**.
4. In the JAR file drop-down menu, click the ellipses ... button to explore your local drive, and select the folder to which you want to **export your JAR deployable file**. (You can also choose Include Project Modules and Dependencies.)

# To Build the Image.
This dockerfile will build a basic image with the mule runtime 3.9 package and the required software package to run the mule application.
   Syntax:
        docker build -t <<name your image>> .
   Example:
        docker build -t salokheanup/mule3.9 .
    - "-t" will tag your image with the provided name 
    - "." will expect the Dockerfile to be present in the root folder from where you are running this command.  

# To Run the Container
Image built in the above step can run a mule standalone server. To run a specific application we need to mount the host directory to container which will automatically build and deploy the application zip file. 
    **Syntax:**
        docker run --name <<NameURContainer> -p <<hostport>>/<<TargetPort>> -v <<host path to mount>>/<<Target dir path to mount>> <<imageID/RepositoryName>>
    **Example:**
    docker run -it --name mymulecontainer -p 80:8081 -v /home/anup/docker/mule/apps/is:/opt/mule/apps -v /home/anup/docker/mule/logs:/opt/mule/logs salokheanup/mule3.9

    - Application expected to run in the container needs to be present in the below folder which is mounted during runtime. "/home/anup/docker_samples/mule/muledockerdemo/myapps/is".
    - Application and domain logs will be stored in the mount point. "/home/anup/docker_samples/mule/muledockerdemo/logs"
    
# URL to Test the service. 
    **Syntax :** 
        http://<<host>>:<<port>>/<<Path of your running application>>
    **Example:**
        http://localhost:80/demo
  -localhost in case you are running the container on your localhost or the specific IP address of the container
  -Host port 80 is exposed during runtime of the container
