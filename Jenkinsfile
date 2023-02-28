node {
    stage('Checkout') {
        git branch: 'main', url: '/home/wasadmin/Software/repos/Ironmaven_auth.git'
    }
    
    stage('Gradle build') {
        sh 'gradle build'
    }
       stage('User Acceptance Test') {
    	def response = input message: 'Is this build good to go?',
    	parameters:[choice(choices: 'Yes\nNo',
    	description: '', name: 'Pass')]
    	
    	if(response=="Yes"){
    		stage ('Release') {
    			sh 'gradle build -x test'
    			sh 'echo DataService is ready to release!'
    			}
    		}
    	}
}