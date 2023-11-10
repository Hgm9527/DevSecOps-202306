Jenkins Setup:
  https://phoenixnap.com/kb/install-jenkins-ubuntu

Step 1: Install Java
    
Update apt
  sudo apt udpate
Install OpenJDK 11
  sudo apt install openjdk-11-jdk -y

Step 2: Add Jenkins Repository

1. Start by importing the GPG key. The GPG key verifies package integrity but there is no output. Run:

curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null

2. Add the Jenkins software repository to the source list and provide the authentication key:
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

Step 3: Install Jenkins
1. Update the system repository one more time. Updating refreshes the cache and makes the system aware of the new Jenkins repository.

sudo apt update

2. Install Jenkins by running:

sudo apt install jenkins -y

3. To check if Jenkins is installed and running, run the following command:

sudo systemctl status jenkins

Note: If the Jenkins service is not running or active, run the following command to start it:

sudo systemctl enable --now jenkins

Step 5: Set up Jenkins
Follow the steps below to set up Jenkins and start using it:

1. Open a web browser, and navigate to your server' IP address. Use the following syntax:

http://ip_address_or_domain:8080

2. Obtain the default Jenkins unlock password by opening the terminal and running the following command:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Obtaining the Jenkins administrator password.
3. The system returns an alphanumeric code. Enter that code in the Administrator password field and click Continue.

4. The setup prompts to either Install suggested plugins or Select plugins to install. It’s fine to simply install the suggested plugins.

5. The next step is the Create First Admin User. Enter the credentials you want to use for your Jenkins administrator, then click Save and Continue.



######

### Run the below commands to install Java and Jenkins

Install Java

```
sudo apt update
sudo apt install openjdk-11-jre
```

Verify Java is Installed

```
java -version
```

Now, you can proceed with installing Jenkins

```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

**Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

- EC2 > Instances > Click on <Instance-ID>
- In the bottom tabs -> Click on Security
- Security groups
- Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed `All traffic`).


