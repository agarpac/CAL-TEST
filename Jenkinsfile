pipeline {
    agent any

    stages {
        stage('Always') { 
            steps {
                echo 'Aqui va a entrar siempre... Hola mundo!'
            }
        }
        stage('Branch develop or PR') {
            when {
                anyOf { 
                    branch 'develop'
                    changeRequest target: 'develop'
                }
            }
            steps {
                echo 'Aqui debe entrar si es rama develop o un PR!'
            }
        }
        stage('Only Branch Master') {
            when{
                branch 'master'
            }
            input {
                message "Should we continue?"
                parameters {
                    choice(name: 'deployMaster', choices: ['no', 'yes'], description: 'Deploy Master branch?')
                }
            }
            steps {
                echo 'Ha tenido que entrar aquí solo al ser rama master'
            }
        }
        stage('Only PR') {
            when{
                changeRequest target: 'develop' 
            }
            steps {
                echo 'Ha tenido que entrar aquí solo si es un PR'
                echo 'Postman - Newman'
            }
        }
    }
}
