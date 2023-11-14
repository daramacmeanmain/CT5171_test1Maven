pipeline {
    agent any

    stages {
        stage('GetProject') {
            steps {
                git 'https://github.com/daramacmeanmain/CT5171_test1Maven.git'
            }
        }

        stage('Build') {
            steps {
                sh "mvn clean:clean"

                sh "mvn dependency:copy-dependencies"

                sh "mvn compiler:compile"
            }
        }

        stage('Exec') {
            steps {
                sh "mvn exec:java"
            }
        }

        stage('Package') {
            steps {
                sh "mvn package"
            }
        }
    }
    post {
        success {
            archiveArtifacts allowEmptyArchive: true,
            artifacts: '**/ct5171_test1Maven*.jar'
        }
    }
}