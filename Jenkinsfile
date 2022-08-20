pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
            }
        }
        stage('Upload War To Nexus'){
            steps{
                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                            file: 'target/simple-app-1.0.0.war', 
                            type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus', 
                    groupId: 'in.javahome', 
                    nexusUrl: '20.187.83.10', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://20.187.83.10:8081/repository/simpleapp/', 
                    version: '1.0.0'
                    
                    }
            }
        }
}
