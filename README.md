# eksgitactions 234

1. <h3> Running this app in docker instructions</h3>
   
  $ git clone <url of this repository>
  $  docker build -t pythonapp1 .
  
to see output on browser we need to expose port 8080 run the below command
  
  $ docker run --name my-container -d -p 8080:8080 pythonapp1 
  
  
  Now visit http://localhost:8080
  
  2. <h3> building docker image and pushing it into Amazon ECR using github actions</h3>
  
  open folder .github/workflows/aws.yml
  
  before starting we need some requirements
    1. AWS account
    2. create ECR repository 
    3.  store aws keys in secretes of github current repository under settings you can find secretes
 
 after this you can edit repository name and aws-region
 then commit you can see it triggers Actions 
 
 
 3. <h3> deploy our app into eks cluster using github actions pipeline </h3>
 
 before proceding into this we need to create cluster
 
 i am deploying the cluster using eksctl
 
 so install eksctl follow instructions of aws https://docs.aws.amazon.com/eks/latest/userguide/getting-started-console.html
 
 it takes several minutes to complete to finish the task
 
 once done  don't forget to update kubeconfig file using below command using aws cli (i believe you already installed and configured)
 
 $ aws eks --region ap-south-1 update-kubeconfig --name first-eks (your cluster name here)
 
 Then create or updATE your deployment.yml and service.yml under manifests folder
 
 
 4. <h3>  Setting up Kubectl for  AWS EKS </h3>
 
   > check in EKS cluster kubernetes version mine is 1.17
   > then 
   execute below commands from your working PC
   
   > $  curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.17.9/2020-08-04/bin/darwin/amd64/kubectl
   > verfying kubectl 
      $ kubectl version --short --client
   > then make sure you updated the kube config file and having correct IAM permissions
 now you can interact with your AWS EKS cluster from your PC
 
 once done execute below commands
 $ kubectl get svc
 $ kubectl describe svc python-svc                            #(your service name) 
 
 then copy external Ip and paste it in browser you can see the output
   
   
 
 
 
 
 
  
  
  
