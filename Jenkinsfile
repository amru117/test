pipeline{
  agent any
  stages{
    stage("creating the docker container c2 for index1 file in master1 branch"){
      steps{
        sh "docker run -dp 90:80 --name c2 httpd"
      }
    }
    stage("give access to the index1 file in the jenkins workspace folder"){
      steps{
        dir('/root/.jenkins/workspace/job_master1'){
          sh "chmod -R 777 index1.html"
        }
      }
    }
    stage("copying the index1 file to htdocs location in the container"){
      steps{
        sh "docker cp /root/.jenkins/workspace/job_master1/index1.html c2:/usr/local/apache2/htdocs"
      }
    }
  }
}
