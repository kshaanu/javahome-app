node('docker-test'){
    def dockerImage = "bhuvanakadiveti/sample:1.0"
    deleteDir()
    stage('Checkout'){
        
        git 'https://github.com/Bhuvana0509/javahome-app'
    }
    
    
    stage('Build Docker Image'){
        sh "sudo apt-get clean"
        sh "docker build -t ${dockerImage} ."
    }
    
    stage('Push image to registry'){
		withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'dockerHubUser', passwordVariable: "dockerHubPassword")]) {
      sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
		
          sh 'docker push ${dockerImage}'
		}
    }
  
}
