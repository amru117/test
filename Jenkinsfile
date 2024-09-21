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
           dir('/root/.jenkins/workspace/job/') {
             sh "chmod -R 777 index.html"
    // some block
}
          }
      }
          
  }
}
