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
		withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerhubPwd')]) {
      //sh "docker login -u bhuvanakadiveti -p ${dockerhubPwd}"
		}
        
        sh "docker push ${dockerImage}"
    }
  
}
