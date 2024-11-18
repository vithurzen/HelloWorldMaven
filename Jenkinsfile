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
                    sh 'git push https://vithurzen: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@github.com/vithurzen/HelloWorldMaven.git $GIT_TAG'
                }
            }
        }
    }
}
