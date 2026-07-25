pipeline {
    agent {
        label 'pipeline'
    }
triggers { pollscm('0 0 * * *')}
tools {
    jdk 'jdk-17'
    maven 'mvn-3.9.12'
}    
parammeters {
    choice(name: 'goals' ,choices: ['mvn package', 'mvn clean', 'mvn validate', 'mvn test'])
    }
    stages{
        stage('git clone'){
            git branch: 'main', url: 'https://github.com/bayyasahhass-hue/spring-petclinic.git'     }
    }
}
stage('mvn build'){
    steps{
        sh "${params.goals}"
    }
}   
