pipeline {

    agent any

    tools {
        maven 'Maven'
        jdk 'JDK21'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Ritabrata123github/Jenkins_Maven_Build'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run JUnit Tests') {
            steps {
                sh 'mvn test'
            }
        }

      stage('SonarQube Analysis') {
    steps {
        withSonarQubeEnv('SonarServer') {
            sh 'mvn sonar:sonar -Dsonar.java.binaries=target/classes'
        }
    }
}

    }
}
