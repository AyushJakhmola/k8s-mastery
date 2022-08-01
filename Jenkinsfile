pipeline{
agent any
  environment{
    Image_Repo="rohitsquareops"
    Branch="master"
  }
stages{
  stage('Go to repo'){
    steps{
      container('docker'){ 
        script{
             echo "take code from github"
             sh '''
              git clone -b $Branch https://github.com/RohitSquareops/k8s-mastery.git
             '''
             echo "Branch copied"
        }
      }
    }
  }
  stage("Build Image and push to dockerhub"){
    steps{
      container('docker'){
        echo "Test code from github"
       sh ''' 
        cd k8s-mastery/sa-frontend
        docker build -t frontendgit .
        docker image tag frontendgit:latest $ImageRepo/frontendgit:latest
        docker push $ImageRepo/frontendgit:latest
       '''
      }
    }
  }
 }
}