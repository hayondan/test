pipeline {
    environment {
    dockerImage = ''
  }
        stage('build and push image') {
            steps {
               script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER“ // give a name and version to image
                    docker.withRegistry('', registryCredential) {
                    dockerImage.push() // push image to hub
                }
            }
        }
         post {
         always {
             bat "docker rmi $registry:$BUILD_NUMBER“ // delete the local image at the end
}}}
