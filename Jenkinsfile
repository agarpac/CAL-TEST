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
                script {
                    // Show the select input modal
                    def INPUT_PARAMS = input message: 'Should we continue?', ok: 'Next',
                                       parameters: [choice(name: 'deployMaster', choices: ['no', 'yes'], description: 'Choose an option and continue')]
                
                    if ('${deployMaster}' == 'yes') {
                        echo 'Ha tenido que entrar aquí solo al ser rama master y confirmando el stage'
                    }
                    if ('${params.deployMaster}' == 'yes') {
                        echo '2Ha tenido que entrar aquí solo al ser rama master y confirmando el stage'
                    }
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
