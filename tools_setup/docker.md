https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04

Step 1 — Installing Docker

    First, update your existing list of packages:

sudo apt update
    Next, install a few prerequisite packages which let apt use packages over HTTPS:

sudo apt install apt-transport-https ca-certificates curl software-properties-common

    Then add the GPG key for the official Docker repository to your system:

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

    Add the Docker repository to APT sources:

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    Update your existing list of packages again for the addition to be recognized:

sudo apt update
    Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:

apt-cache policy docker-ce

    Finally, install Docker:

sudo apt install docker-ce
    Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:

sudo systemctl status docker

sudo systemctl enable docker

Step 2 — Executing the Docker Command Without Sudo (Optional)

    If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group:

sudo usermod -aG docker ${USER}
    To apply the new group membership, log out of the server and back in, or type the following:

su - ${USER}
    You will be prompted to enter your user’s password to continue.

    Confirm that your user is now added to the docker group by typing:

groups
Output
sammy sudo docker
If you need to add a user to the docker group that you’re not logged in as, declare that username explicitly using:

sudo usermod -aG docker username


sudo apt install -y docker-compose
