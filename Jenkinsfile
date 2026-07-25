pipeline {
    agent {
        label 'spc_pipeline'
    }

    triggers {
        pollSCM('0 0 * * *')
    }

    tools {
        jdk 'jdk-17'
        maven 'mvn-3.9.12'
    }

    parameters {
        choice(
            name: 'GOALS',
            choices: [
                'clean',
                'validate',
                'test',
                'package'
            ],
            description: 'Select Maven Goal'
        )
    }

    stages {

        stage('Git Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/kasagonirithish/spring-petclinic.git'
            }
        }

        stage('Maven Build') {
            steps {
                sh "mvn ${params.GOALS}"
            }
        }

        
        }
    }
}