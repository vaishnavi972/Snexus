node('master') 
{
    stage('ContinuousDownload')
    {
            git 'https://github.com/vaishnavi972/maven.git'
    }
    stage('ContinuousBuild') 
    {
            sh 'mvn package'
    }
    stage('Upload War To Nexus') 
    {
    nexusArtifactUploader artifacts: [
        [
            artifactId: 'maven-project', 
            classifier: '', 
            file: '/home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war',
            type: 'war'
        ]
    ],
    credentialsId: 'nexus_cred',
    groupId: 'com.example.maven-project', 
    nexusUrl: '3.238.132.244:8081', 
    nexusVersion: 'nexus3', 
    protocol: 'http', 
    repository: 'maven-project', 
    version: '2.0'
    }
} 