pipeline{
 agent any
 stages{
 stage ('Checkout') {
 steps{
    checkout scm
 }
 }
 stage('Restore') {
			steps {
			bat "dotnet restore"
			}
		}
stage('Build') {
			steps {
                bat 'dotnet build --configuration Release'
			}
		}
        stage('Test') {
			steps {
                bat 'dotnet test --no-restore --configuration Release'
			}
		}
stage('Publish') {
			steps {
                bat 'dotnet publish --no-restore --configuration Release --output .\\publish'
			}
		}

stage("Deployment") {
            steps {
                              bat '''
                        if exist "C:\\inetpub\\wwwroot\\WebAppIISPipe" rmdir /q /s "C:\\inetpub\\wwwroot\\WebAppIISPipe"
                        mkdir "C:\\inetpub\\wwwroot\\WebApp"
                    '''
                bat "C:\\Windows\\System32\\xcopy.exe /E /Y /I publish\\* C:\\inetpub\\wwwroot\\WebAppIISPipe\\"
            }
        }
    }
    post {
        success {
            echo "Build, Test, Publish Stages Completed Successfully."
        }
    }
}