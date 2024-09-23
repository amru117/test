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
    stage("creating the docker container on the slave machine"){
      steps{
        sh "sudo docker run -dp 80:80 --name c1 httpd"
      }
    }
    stage("giving access to the index file present in the .jenkins folder after running the job"){
      steps{
        dir('/mnt/jenkins-slave/workspace/job_master'){
          sh "sudo chmod -R 777 index.html"
        }
      }
    }
    stage("copying the index file to the server location in the container"){
      steps{
        sh "sudo docker cp /mnt/jenkins-slave/workspace/job_master/index.html c1:/usr/local/apache2/htdocs"
      }
    }
  }
}
