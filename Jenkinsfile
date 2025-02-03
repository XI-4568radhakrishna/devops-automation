pipeline {
    agent any
    tools{
        maven 'maven3.9.9'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/XI-4568radhakrishna/devops-automation.git']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t javatechie/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'DockerHubcreds', variable: 'DockerHubcreds')]) {
                   sh 'docker login -u radhakrishnamopuru459 -p ${Gandhirkm@123}'

}
                   sh 'docker push javatechie/devops-integration'
                }
            }
        }
                
    }
}
