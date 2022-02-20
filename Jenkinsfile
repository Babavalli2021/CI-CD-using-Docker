pipeline {
    agent any
	
	 tools {
  maven 'maven'
}

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/devops4solutions/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp babavalli/samplewebapp:latest'
                //sh 'docker tag samplewebapp babavalli/samplewebapp:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
          sh  'docker push babavalli/samplewebapp:latest'
        //  sh  'docker push babavalli/samplewebapp:$BUILD_NUMBER' 
        }
                  
          }
        }
     
 
        }
    }

    
