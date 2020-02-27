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
            steps {
                milestone(1)
                timeout(time: 5, unit: 'MINUTES') {
                    input 'Master deploy, are you sure?'
                }
                milestone(2)
                script {
                    echo 'Ha tenido que entrar aquí solo al ser rama master y confirmando el stage' 
                }
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
