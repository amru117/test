pipeline{
  agent{
    label "slave2"
  }
  stages{
    stage("install docker and start the service"){
      steps{
        sh "sudo yum install docker -y"
        sh "sudo systemctl start docker"
      }
    }
    stage("creating the container with apache to deploy the index file from master1 branch"){
      steps{
        sh "sudo docker run -dp 80:80 --name c2 httpd"
      }
    }
    stage("giving access to the index file"){
      steps{
        
      }
    }
 
  }
}
