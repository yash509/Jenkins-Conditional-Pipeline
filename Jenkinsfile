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




--------------------------------------- 2nd way for the Work using the below Pipeline----------------------------------------------------------------------------


pipeline {
    agent {
        node {
            label "stapp01"
            customWorkspace '/var/www/html'
        }
    }
    
    parameters{
        string (
            name: 'BRANCH',
            defaultValue: 'master',
            description: 'Branch to deploy (master or feature)'
        )
    }

    stages {
        stage('Deploy') {
            steps {
                dir('web_app'){
                    script {
                        if (params.BRANCH != 'master' && params.BRANCH != 'feature'){
                        error("Invalid BRANCH parameter. Only master or feature are allowed")
                    }
        
                    sh """
                    git fetch origin
                    git checkout ${params.BRANCH}
                    git pull origin ${params.BRANCH}
                    """ 
                    }
                }
            }
        }
    }
}



