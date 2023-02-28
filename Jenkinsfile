node {
    stage('Checkout') {
        git branch: 'main', url: '/home/wasadmin/Software/repos/Ironmaven_auth.git'
    }
    
    stage('Gradle build') {
        sh 'gradle build'
    }
}