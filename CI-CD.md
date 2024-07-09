Contionous Integration or Contionous Delivery


to deliver applications we need to unit testing, static code analysis, code quality/vulnarability,Fuctional testing/automation, reports,deployment all these steps are needed.
--------------------

Unit Testing: suppose we have testing the a caliculator app for addition, we check by passing 2 and 3 and see 5 is comimg or not. we check that particular block 
static code analysis: to check we are syntaxically correct, to check unused variables like we have deaclared 20 variables but we use only 2 for calculator, indentation and well formated code or not
code quality/vunerability: to check security for vunarability to move from one statge to another
Functional testing: we check this function does not effects other functions, like addition function does not effct subtract. also we do end to end testing
Reports: how many unitests passed, what is code quality is it passed or not.
deployment: where customer can access your applications.

----------------------------------------------------------
we create jira story for each functinality/feature like for addition and store each functionality we store in git repo. suppose i will write version1 of additionand version 2.... till version 15 when
we are satisfied with version15 we may decide to make it live for customer.

we will deploy a CICD tool like jenkins to monitor if there is any commit in git repo or branch. jenkins will acts as a orchesator/pipelines.

jenkins will use many tools for this ci-cd like for jave it uses maven for building, junit for unit testing, sonar for code quality, ALM for reporting, for deployment k8/dcoker/ec2.

jenkins also promote from dev to staging whenever it is good finnaly it can promote to production by manual approval or automatic approval.

first we test in dev there may ne one instance, staging  we may have cluster 3 master or 5 worker node in staging,  in production we will have 3 master and 30 worker nodes.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
jenkins is nothing but binary,

in real time there will be 1000s of micro services, to deploy this microservices jenkins is a platform.we will install jenkins on one host/ec2 and we keep adding machines to it because there are 100 of developers 
as one jenkins cant handle 100 dev or 10 teams. lets we say for team1 run in node1 and for team 2 work in node2.


if we add compute to jenkins it will be costly setup and also maintaince becomes huge. so we need to make setup that will scaleup and scaledown automatically. let says we want in weekend our jenkins node to be completely zero
there is zero code changes and there are 20 jenkins setup usally(3 master and 15 worker nodes) in such cases jenkins is not tool we reccomend.


let us look at modern opensource approach like kubernetes.

we ever developer is making commit in any of the repositories ,u can create a pod in k8s on a cluster once execution is done delete the pod later any other can use this cluster.
instead wasting resources for each and every project we can create one github action which can be used by multiple people/projects in the organization. so that we can save our resources. we are using zero resources 
when there is no code changes.

using git hub actions we can integrate it from one project to another project as well.

to install jenkins:
sudo apt update -y
sudo apt install openjdk-17-jre -y

java -version

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

sudo apt update -y

ps -ef | grep jenkins

to copy from go to this path: sudo cat  /var/lib/jenkins/secrets/initialAdminPassword

----------------------------------------------------------------------------------------------

Install the Docker Pipeline plugin in Jenkins:
Log in to Jenkins.
Go to Manage Jenkins > Manage Plugins.
In the Available tab, search for "Docker Pipeline".
Select the plugin and click the Install button.
Restart Jenkins after the plugin is installed.

-----------------------------------------------------------------------------------------------
dev3-Rameshat1276
--------------------------------------------------------------------------------------

Docker Slave Configuration:
Run the below command to Install Docker

sudo apt update
sudo apt install docker.io

Grant Jenkins user and Ubuntu user permission to docker deamon:
(note: without giving permissions for ubuntu and jenkins for docker the build will not happen)
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker
--------------------------------------------------------------------------------------------------


<img src="https://github.com/dev1287/devops/blob/main/images/jenkins/1.png" alt="Screenshot 2023-02-01 at 5 46 14 PM" style="max-width: 100%;">

after creating pipeline you can see docker images for sometime and which automatically deletes after sometime.

































