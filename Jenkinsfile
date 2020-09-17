pipeline{
  agent any
  stages{
    stage('Clone Repository'){
      steps{
        sh '''
        sudo apt update | sudo apt install git 
        git clone https://gitlab.com/qacdevops/chaperootodo_client
        cd chaperootodo_client
        pwd
        '''
      }
    }
    stage('Install Docker and Docker-Compose'){
      steps{
        sh '''
        curl https://get.docker.com | sudo bash 
        sudo usermod -aG docker $(whoami) 
        sudo curl -L https://github.com/docker/compose/releases/download/1.27.3/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
        sudo chmod +x /usr/local/bin/docker-compose
        '''    
      }
    }
    stage('Deploy application'){
      steps{
        sh "pwd && sudo docker-compose up -d"
      }
    }
  }
}  
