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
                'mvn package',
                'mvn clean',
                'mvn validate',
                'mvn test'
            ]
        )
    }

    stages {

        stage('Git Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/kasagonirithish/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh "${params.GOALS}"
            }
        }

        stage('Deploy') {
            steps {
                sh 'nohup java -jar target/spring-petclinic-2.7.3.jar > app.log 2>&1 &'
            }
        }
    }
}