String cron_string = BRANCH_NAME == "master" ? "* * * * *" : ""

pipeline {
    triggers { cron(cron_string) }
  
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
