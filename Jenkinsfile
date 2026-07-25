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
            choices: ['mvn package', 'mvn clean', 'mvn validate', 'mvn test'],
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
        stage('deploy') {
            steps {
                sh "java -jar /home/ubuntu/spc/workspace/pipeline_spc/target/spring-petclinic-3.0.0-SNAPSHOT.jar"
            }
        }

    }
}