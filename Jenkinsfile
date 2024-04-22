pipeline {
    agent any

    tools {
        maven 'Maven' // Skonfigurowane w globalnej konfiguracji narzędzi Jenkinsa jako 'maven'
        jdk 'Java' // Skonfigurowane w globalnej konfiguracji narzędzi Jenkins jako 'java'
    }

    environment {
        // Zdefiniowanie JAVA_HOME może być opcjonalne, w zależności od konfiguracji Jenkinsa.
        JAVA_HOME = tool 'Java'
    }


    stages {
        stage('Initialize') {
            steps {
                bat 'echo Pipeline started'
            }
        }

        stage('Checkout') {
            steps {
                git url: 'https://github.com/spring-projects/spring-petclinic.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                bat '.\\mvnw.cmd clean package'}
            }
        stage('Test') {
            steps {
                bat '.\\mvnw.cmd test'
            }
        }
        }
        post {
        always {
            junit 'target\\surefire-reports\\*.xml' // Publikuje raport z wynikami testu JUnit
        }
    }
}
