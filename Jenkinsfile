node {
    stage ("Checkout DataService"){
        git branch: 'main', url: 'https://github.com/kineticvenom/Ironmaven_auth.git'
    }
    
    stage ("Gradle Build - DataService") {
	
        sh 'gradle clean build'

    }
    
    stage ("Gradle Bootjar-Package - DataService") {
        sh 'gradle bootjar'
    }
    
    stage ("Containerize the app-docker build - AuthApi") {
    	sh 'docker build --rm -t mcc-auth:v1.0 .'
    }
    
    stage ("Inspect the docker image- AuthApi") {
    	sh "docker run -d --rm --name mcc-auth -p 8081:8081 mcc-auth:v1.0"
    }
    
    stage('User Acceptance Test - DataService') {
	
	  def response= input message: 'Is this build good to go?',
	   parameters: [choice(choices: 'Yes\nNo', 
	   description: '', name: 'Pass')]
	
	  if(response=="Yes") {

	    stage('Release- AuthService') {
	     sh 'docker stop mcc-auth'
	     sh 'echo AuthService is ready to release!'

	    }
	  }
    }
}