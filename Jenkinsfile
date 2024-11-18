pipeline { 
    agent any 
    stages {
        stage('Build') { 
            steps {
                withMaven(maven : 'apache-maven-3.6.0') {
                    sh "mvn clean"
                }
            }
        }
        stage('Test') {
            steps {
                withMaven(maven : 'apache-maven-3.6.0') {
                    sh "mvn package"
                }
            }
        }
        stage('Tag version. release') {
            environment {
                GIT_TAG = "version-2.$BUILD_NUMBER"
            }
            steps {
                script {
                    sh 'git config user.name "vithurzen"'
                    sh 'git config user.email "vithurzen517@gmail.com"'
                    sh 'git tag -a $GIT_TAG -m "[Jenkins CI] New Tag"'
                    sh 'git push origin $GIT_TAG'
                }
            }
        }
    }
}
