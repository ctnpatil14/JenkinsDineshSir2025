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
              powershell '''pwd'''
              powershell '''dir'''
              powershell '''new-Item -Name "chetanapp" -type directory -path "c:\\" -errorAction ignore'''  
              powershell '''cd  "$env:JENKINS_HOME\\workspace\\$env:JOB_NAME\\application\\chetanapp" 
                            write-host "changing directory" 
                            pwd
                            dotnet publish -c Release -o "c:\\chetanapp"
                         ''' 
                         
               
              
              
            }
        }

        stage('publish') {

            steps {
                    powershell '''cd c:\\chetanapp
                                  pwd
                                  dir
                                  Start-Process "dotnet" "chetanapp.dll --url='http://localhost:$env:Port'" -WindowStyle Hidden
                              '''
                    
            }

        }


    }

    post {
         success {
            powershell ''' 
                        write-host " http://localhost:$env:Port "
                        curl http://localhost:$env:Port '''
        }
        failure {
            powershell ''' Write-Host "Build Failed" '''
        }
    }
}

