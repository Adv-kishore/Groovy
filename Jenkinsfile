pipeline {
    agent any
    environment {
    PATH= "/opt/maven/bin:$PATH"
    }
    stages {
        stage("clonig stage"){
            steps{
                git branch: 'main', url: 'https://github.com/Adv-kishore/Groovy.git'
            }
        }
        stage("Building stage"){
            steps{
                sh "mvn clean install"
            }
        }
        stage("Deploying stage"){
            steps{
                sshagent(['7afb13db-6e2e-417d-a2b3-10fcac482b23']) {
                     sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pipeline/target/Project.war ec2-user@13.209.11.245:/opt/tomcat/webapps"
                     }
            }
        }
    }
}
