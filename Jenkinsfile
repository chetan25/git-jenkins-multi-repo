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
                    sh 'git checkout -b "version-update-1"'
                    sh 'gh release list'
                    sh 'npm ci'
                    sh 'npm install react@v16.0.0'
                    sh 'git add .'
                    sh 'git commit -m "fix: updated version"'
                    sh 'gh pr create --title "Pull request title" --body "Pull request body"'
                }
            }    
        }
    }
}
