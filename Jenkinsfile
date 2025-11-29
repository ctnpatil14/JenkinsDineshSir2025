/* groovylint-disable-next-line CompileStatic */
pipeline {
   agent any
    
    environment {

        Port = 5030
    }

    stage('checkout') {

            steps {
                    checkout scmGit(branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/ctnpatil14/JenkinsDineshSir2025.git']])
                    
            }

        }

    

        stage ('build') {
            steps {

               powershell '''dotnet publish -c Release -o "c:\\chetanapp"'''
            }
        }

        stage('publish') {

            steps {
                    powershell '''dotnet chetanapp.dll --url="http://localhost.${env.Port}"'''
                    
            }

        }


    }


