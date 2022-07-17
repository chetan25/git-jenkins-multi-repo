pipeline {
    agent any

    tools {nodejs "Node"}

    environment {
        GITHUB_TOKEN = credentials('jenkins-git')
    }
    stages {
        stage('DraftPR') {
            steps {
               script { 
                    echo 'Starting Draft PR'
                    sh "echo ${params.Version}"
                    sh 'gh release list'
                    sh 'npm ci'
                    sh 'npm run s:release'
                }
            }
        }
    }
}
