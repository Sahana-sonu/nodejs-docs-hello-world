pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        
        
       stage ('Verify') {

           steps {
               sh "mvn clean verify sonar:sonar \
              -Dsonar.projectKey=ProjectSon \
              -Dsonar.host.url=http://52.187.151.43:9000 \
              -Dsonar.login=sqp_a3c65ee4294eab98e69142832e123b9d5c0646dc"
           }
       }

    }
    
    post {
        success {
            echo 'Node.js project built, tested, and analyzed successfully!'
        }
        failure {
            echo 'Build, test, or analysis failed. Check the logs for details.'
        }
    }
}
