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



 }



}