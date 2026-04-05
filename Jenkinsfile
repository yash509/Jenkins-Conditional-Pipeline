pipeline {
    agent {
        label "stapp01"
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    if (params.BRANCH != 'master' && params.BRANCH != 'feature'){
                        error("Invalid BRANCH parameter. Only master or feature are allowed")
                    }
                    git branch: "${params.BRANCH}",
                        url: "https://3000-port-hah6y7qoyg2zl45s.labs.kodekloud.com/sarah/web_app.git"
                        
                    sh '''
                        cp -r * /var/www/html/
                    '''    
                }
            }
        }
    }
}
