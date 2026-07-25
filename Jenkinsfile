pipeline {
    agent {
        label 'pipeline'
    }

    triggers {
        pollSCM('0 0 * * *')
    }

    tools {
        jdk 'jdk-17'
        maven 'mvn'
    }

    parameters {
        choice(
            name: 'GOALS',
            choices: ['clean', 'validate', 'test', 'clean package'],
            description: 'Select Maven Goal'
        )
    }

    stages {

        stage('Git Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/bayyasahhass-hue/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh "mvn ${params.GOALS}"
            }
        }

    }
}