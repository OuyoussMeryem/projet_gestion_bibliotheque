pipeline {
    agent any
    environment {
        MAVEN_HOME = tool 'Maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/OuyoussMeryem/projet_gestion_bibliotheque.git'
            }
        }
        stage('Build') {
            steps {
                bat "\"${MAVEN_HOME}\\bin\\mvn\" clean compile"
            }
        }
        stage('Test') {
            steps {
                bat "\"${MAVEN_HOME}\\bin\\mvn\" test"
            }
        }
        stage('Quality Analysis') {
            steps {
                withSonarQubeEnv('sonarqube_server') {
                    bat "\"${MAVEN_HOME}\\bin\\mvn\" sonar:sonar"
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Simulated deployment successful'
            }
        }
    }
    
}
