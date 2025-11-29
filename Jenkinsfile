/* groovylint-disable-next-line CompileStatic */
pipeline {
   
   agent any
    
    environment {

        Port = 5030
    }

    stages {

        stage('checkout') {

            steps {
                    checkout scmGit(branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/ctnpatil14/JenkinsDineshSir2025.git']])
                    
            }

        }

    

        stage ('build') {
            steps {
              sh ' pwd '
              sh ' ls -lrt'
               powershell '''dotnet publish -c Release -o "c:\\chetanapp"'''
            }
        }

        stage('publish') {

            steps {
                    sh ' pwd '
                    sh ' ls -lrt'
                    powershell '''dotnet chetanapp.dll --url="http://localhost.${env.Port}"'''
                    
            }

        }


    }
}

