pipeline {
    agent any

    stages {
        stage('Always') { 
            steps {
                echo 'Aqui va a entrar siempre... Hola mundo!'
            }
        }
        stage('Branch testSonar or PR') {
            when {
                anyOf { 
                    branch 'testSonar'
                    //expression { env.BUILDCAUSE =~ /.*PR.*/ }
                    changeRequest ()
                    //allOf{
                        //changeRequest () ; 
                        //expression { return (GIT_BRANCH != 'origin/testAgarrido') }
                    //}
                }
            }
            steps {
                echo 'Aqui debe entrar si es rama testSonar o un PR!'
            }
        }
        stage('Only Branch testSonar') {
            when{
                branch 'testSonar'
            }
            steps {
                echo 'Ha tenido que entrar aquí solo por ser rama testSonar'
            }
        }
        stage('Only Branch Master') {
            when{
                branch 'master'
            }
            steps {
                echo 'Ha tenido que entrar aquí solo al ser rama master'
            }
        }
        stage('Only PR') {
            steps {
                echo 'Ha tenido que entrar aquí solo si es un PR'
            }
        }
    }
}
