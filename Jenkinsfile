pipeline{
  agent any
  stages{
    stage("copying the index1 file to the path at volume is mounted"){
      steps{
        sh "cp -r /root/.jenkins/workspace/job_master1/index1.html /var/lib/docker/volumes/index/_data"
      }
    }
    stage("giving access to the index1 file present in the path at which volume is mounted"){
      steps{
        dir('/var/lib/docker/volumes/index/_data'){
          sh "chmod -R 777 index1.html"
        }
      }
    }
    stage("creating the container with apache and mount the volume index/var/lib/docker/volumes/index/_data on it and deploy index1 file present in that"){
      steps{
        sh "docker run -dp 90:80 -v index:/usr/local/apache2/htdocs --name c2 httpd"
      }
    }
  }
}
