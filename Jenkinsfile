pipeline {
  agent any
  
  stages {
    stage('Build') {
      steps {
        // Checkout source code from version control
        git 'https://github.com/YASHODA-MUNNANGI/jenkins_docker.git'
        
        
      }
    }
    
    stage('Docker Build') {
      steps {
        // Build the Docker image
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerregistry') {
            def customImage = docker.build('hello-world-java1', '-f Dockerfile .')
            customImage.push()
          }
        }
      }
    }
    
    stage('Deploy') {
      steps {
        // Deploy the Docker container
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerregistry') {
            sh 'docker run -it hello-world-java1'
          }
        }
      }
    }
  }
}
