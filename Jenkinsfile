node('docker'){
    def dockerImage = "anushakakunulla/sample:1.2"
    deleteDir()
    stage('Checkout'){
        
        git 'https://github.com/kshaanu/javahome-app'
    }
    
    
    stage('Build Docker Image'){
        sh "sudo apt-get clean"
	    sh "docker build -t ${dockerImage} ."
    }
   
    stage('Push image to registry'){
		withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'dockerHubUser', passwordVariable: "dockerHubPassword")]) {
      sh 'echo $dockerHubUser'
      sh 'echo $dockerHubPassword'
			
			
      sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
		
          sh "docker push ${dockerImage}"
		}
    }
  
}
