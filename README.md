# mule-docker-demo
This project is to dockerize the mule application 

# To Build the Image
    docker build -t <<name your image>> .
    
    - "-t" will tag your image with the provided name 
    - "." will expect the Dockerfile to be present in the root folder from where you are running this command. 

# To Run the Container
    docker run -it --name <<NameURContainer>> -p 80:8081 -v /home/anup/docker_samples/mule/muledockerdemo/myapps/is:/opt/mule/apps -v /home/anup/docker_samples/mule/muledockerdemo/logs:/opt/mule/logs <<imageID/Name>>

    - Application expected to run in the container needs to be present in the below folder which is mounted during runtime. "/home/anup/docker_samples/mule/muledockerdemo/myapps/is".
    - Application and domain logs will be stored in the mount point. "/home/anup/docker_samples/mule/muledockerdemo/logs"
    
# URL to Test the service. 
    http://localhost:80/demo
  -(localhost in case you are running the container on your localhost)or the specific IP address of the container
  -Host port 80 is exposed during runtime of the container
