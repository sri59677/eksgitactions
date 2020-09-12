# eksgitactions 234

1. <h3> Running this app in docker instructions</h3>
   
   git clone <url of this repository>
  docker build -t pythonapp1 .
  
  to see output on browser we need to expose port 8080 run the below command
  
  docker run --name my-container -d -p 8080:8080 pythonapp1 
  
  
