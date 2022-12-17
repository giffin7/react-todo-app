pipeline {
    agent any
    tools {
        nodejs '17.0.1'
    }
    
    stages {
        stage ('SCM') {
            steps {
                git branch: 'main',url:'https://github.com/giffin7/react-todo-app.git'
            }
        }
        stage ('npm install') {
            steps {
                sh 'npm install'
            }
        }
          stage ('build') {
            steps {
                sh 'npm run build'
            }
         }
          stage('deploy to apache2') {
            steps {
                sh 'sudo cp -rv build/* /var/www/html/'
            }
        }
           stage ('Archive Artifacts') {
        steps {
            sh 'sudo zip -r archive.zip build/*'
             archiveArtifacts artifacts: 'build/*', excludes: '*.log', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
            }
        }
    }
}
