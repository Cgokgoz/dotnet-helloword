pipeline {
    agent {
        docker {image 'appdynamics/dotnet-core-agent'}
    }
     triggers {
        githubPush()
      }
    stages {
        stage('Restore packages'){
           steps{
               sh 'dotnet restore samples-dotnet-helloworld.sln'
            }
         }
        stage('Clean'){
           steps{
               sh 'dotnet clean samples-dotnet-helloworld.sln --configuration Release'
            }
         }
        stage('Build'){
           steps{
               sh 'dotnet build samples-dotnet-helloworld.sln --configuration Release --no-restore'
            }
         }
        stage('Test: Unit Test'){
           steps {
                sh 'dotnet test samples-dotnet-helloworld/samples-dotnet-helloworld.csproj --configuration Release --no-restore'
             }
          }

    }
}
