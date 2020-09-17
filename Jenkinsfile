pipeline{
  agent any
  stages{
    stage('Clone Repository'){
      steps{
        sh '''
        chmod +x repo-clone.sh
        ./repo-clone.sh
        cd chaperootodo_client/
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
        sh "cd chaperootodo_client && sudo docker-compose up -d"
      }
    }
  }
}  
