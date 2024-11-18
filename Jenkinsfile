pipeline { 
    agent any 
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'mvn package'
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
                    withCredentials([usernamePassword(credentialsId: 'token', usernameVariable: 'GIT_USER', passwordVariable: 'GIT_TOKEN')]) {
                        sh "git push https://$git_user/$GIT_TOKEN@github.com/vithurzen/HelloWorldMaven.git $GIT_TAG"
                    }
                }
            }
        }
    }
}
