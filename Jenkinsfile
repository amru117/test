pipeline{
  agent{
    label "slave1"
  }
  stages{
    stage("install docker and start the service"){
      steps{
        sh "sudo yum install docker -y"
        sh "sudo systemctl start docker"
      }
    }
  }
}
