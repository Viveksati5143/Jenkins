pipeline {
    agent any
    environment{
        name = 'vivek'
    }
    parameters{
        string(name: 'person', defaultValue: 'Vivek Sati', description: "Who are you?")
        booleanParam(name: 'isMale', defaultValue: true, description: "")
        choice(name: 'City', choices: ['Jaipur','Mumbai','Pune'], description: "")
    }

    stages {
        stage('Run a command') {
            steps {
                sh '''
                    ls
                    pwd
                    date
                    cal 2022
                '''
            }
        }
        stage('Environment variables') {
            steps {
                sh 'echo Build number: "${%BUILD_NUMBER}"'
                sh 'echo "${name}"'
            }
        }
        stage('Deploy on test') {
            environment{
                username = 'mafia'
            }
            steps {
                echo 'Deploy on test'
                bat 'echo "${username}"'
                bat 'echo "${person}"'
            }
        }
        stage('Continue') {
            input{
                message "Should we continue?"
                ok "Yes we should"
            }
            steps {
                echo 'Deploy on prod'
            }
        }
        stage('Deploy on prod') {
            steps {
                echo 'Deploy on prod'
            }
        }
    }
    post{
        always{
            echo 'This will always deploy'
        }
        failure{
            echo 'Failure'
        }
        success{
            echo 'Success'
        }
    }
}
