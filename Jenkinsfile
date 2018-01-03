pipeline {
    agent any
    tools {
        maven 'apache-maven-3.5.2'
        jdk 'jdk1.8.0_102'
    }
    stages {
        
        stage ('Build') {
            steps {
            bat 'mvn install'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
        
         stage('Sonarqube analysis') {
    steps {
    script {
             scannerHome = tool 'SonarScanner';
        }
     withSonarQubeEnv('SonarQube') {
       bat "${scannerHome}\\bin\\sonar-scanner.bat" 
    }

    } 
        }
    }
}
