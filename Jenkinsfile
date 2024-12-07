pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Lightnoria/Sys-prog-lab4.git', 
                    credentialsId: 'github-token'
            }
        }

        stage('Build') {
            steps {
                bat '"C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /t:Build /p:Configuration=Release'
            }
        }

        stage('Test') {
            steps {
                bat "x64\\Release\\test_repos.exe --gtest_output=xml:test_report.xml"
            }
        }
    }

    post {
        always {
            junit 'test_report.xml'
        }
    }
}
