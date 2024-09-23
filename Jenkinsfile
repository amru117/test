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
        dir('/mnt/jenkins-slave/workspace/job_master1'){
          sh "sudo chmod -R 777 index1.html"
        }
      }
    }
    stage("copying the file into the apache path into the container"){
      steps{
        sh "sudo docker cp /mnt/jenkins-slave/workspace/job_master1/index1.html c2:/usr/local/apache2/htdocs"
      }
    }
 
  }
}
