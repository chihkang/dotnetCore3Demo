pipeline {
    agent any
    environment {
        // dotnet = '/usr/local/share/dotnet'
        //PROJECT_NAME='RestAPI'
    }
    stages{
        stage('clone from github repo') {
            steps{
                git branch: 'master', url: 'https://github.com/chihkang/dotnetCore3Demo.git'
            }
        }

// 		stage("dir") {
// 			steps{
// 			    println env.WORKSPACE
// 			    dir("${env.WORKSPACE}/test"){
// 			    }
// 			}
// 		}

        stage('dotnet restore') {
            steps{
                 //sh("dotnet build ./${PROJECT_NAME}")
		sh("dotnet build")
            }
        }
        stage('dotnet publish'){
            steps{
                // withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {
                sh(script:"dotnet publish -o /Users/chihkang/Desktop/jenkins-practice/pipeline", returnStdout: true)
                // }
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
