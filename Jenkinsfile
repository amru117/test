pipeline{
  agent any
  stages{
    stage("create the voluem"){
      steps{
        sh "docker volume create index"
      }
    }
    stage("giving access to the index file"){
      steps{
        dir('/root/.jenkins/workspace/job_master/'){
          sh "chmod -R 777 index.html"
        }
      }
    }
    stage("copy the index file to mount point of volume"){
      steps{
        sh "cp -r /root/.jenkins/workspace/job_master/index.html /var/lib/docker/volumes/index/_data"
      }
    }
    stage("creating the container with apache on which the volume will mount"){
      steps{
        sh "docker run -dp 80:80 -v index:/usr/local/apache2/htdocs --name c1 httpd"
      }
    }
  }
}
