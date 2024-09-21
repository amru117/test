pipeline{
  agent any
  stages{
    stage("creating apache container c1 run on the port 80"){
      steps{
        sh "docker run -dp 80:80 --name c1 httpd"
      }
    }
    stage("giving access to the index file in the jenkins job location"){
          steps{
           dir('/root/.jenkins/workspace/job_master/') {
             sh "chmod -R 777 index.html"
    // some block
}
          }
      }
      stage("copy the index file to htdocs location in the docker"){
        steps{
          sh "docker cp /root/.jenkins/workspace/job_mater/index.html c1:/usr/local/apache2/htdocs"
        }
      }
  }
}
