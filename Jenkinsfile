pipeline {
    agent any
    
    tools {nodejs "Node12x"}
    
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git url: 'https://github.com/gumalheiros/AngularAppGitHub.git', branch:'dev'

                // Instala o NPM.
                sh "npm install"
                
                // Instala o NPM.
                sh "npm run build"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the zip file.
                success {
                    script {
                        zip zipFile: 'drop.zip', archive: true, dir: 'dist/angularapp'
                    }
                }
            }
        }
    }
}
