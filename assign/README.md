# Deploy a REST API into Amazon Document DB Cluster using AWS Cloud Formation. API should be exposed through Amazon API Gateway and AWS Lambda.

<br/>

# Steps for Deploy a REST API

<br /> <hr> <br />

First we have to use a template or code. So , I used this one 

```
git clone https://github.com/aws-samples/docdb-rest.git
```
![Click on this ](./assets/1.png)

We need to build the .zip file for the Lambda layer that holds the database driver and certificate authority file to connect to Amazon DocumentDB. 

```
make
```

After that we have to build the serverless application via the sam command . But before we have to  install the sam command in our Env.
```
brew install aws-sam-cli 
sam --version 
```
![Click on this ](./assets/2.png) 
![Click on this ](./assets/3.png) 

After installation of **sam** when I run **make** Its showing me error for python runtime version mismatch. when I search for supported version ,Its only support some python version As we can see in below Screenshot . But In my Mac I have installed python3.10 version , For deploy the Lamba function I installed the downgrade python3.8 version .

![Click on this ](./assets/4.png) 

After that when I run **make** , Its showing again same error . To solve that error have to changes in 2 configuration files in template code. First I changed in **template.yaml** file , I changed the python version 3.6 to 3.8 . 

![Click on this ](./assets/5.png) 

For runtime python version have to change in **Makefile** file , because when I run Make its run from 3.8 version. 

![Click on this ](./assets/6.png) 

After that I run **make** its run succesfully .

Now you’re ready to build the serverless application via the sam command

```
sam build
```
![Click on this ](./assets/7.png) 

When that is complete, deploy the serverless application

```
sam deploy --capabilities akash --guided
```

We need to answer several questions from the command line:
 
 ![Click on this ](./assets/9.png) 

After giving the all requirements Its giving the error for credentials , Because I dont have permission to create a IAM user in Udemy Workspace . 

![Click on this ](./assets/10.png) 