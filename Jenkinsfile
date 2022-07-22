pipeline {
    agent any

    tools {nodejs "Node"}

    environment {
        GITHUB_TOKEN = credentials('jenkins-git')
    }
    stages {
        stage('Create DraftPR') {
            steps {
                script { 
                    echo 'Starting Draft PR'
                    sh "echo With Version: ${params.VERSION}"
                    sh "echo Checking out PR Branch Name ${params.PR_NAME}"
                    sh "git checkout -b ${params.PR_NAME}"
                    // for test purposes installing react version
                    sh 'npm install react@v16.0.0'
                    sh "echo Adding changed package file"
                    sh 'git add package.json package-lock.json'
                    sh 'git commit -m "fix: updated version"'
                    sh "git push --set-upstream origin ${params.PR_NAME}"
                    sh 'gh pr create --title "version-update" --body "Pull request body"'
                }
            }    
        }
    }
}
