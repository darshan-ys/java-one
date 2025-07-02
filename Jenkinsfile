pipeline
{
    agent any 
    tools {
  maven 'maven3'
}   
options {
  buildDiscarder logRotator(daysToKeepStr: '10', numToKeepStr: '7')
}
parameters {
  choice choices: ['develop', 'qa', 'master'], description: 'choices the branch to build', name: 'branch'
}

    stages
    {
        stage('Git Clone'){
            steps{
                git branch: 'develop', url: 'https://github.com/darshan-ys/java-one'
            }
        }
        stage('Maven Build'){
            steps{
                sh 'mvn clean package'
            }
        }
    }
    post {
  success {
    archiveArtifacts artifacts: 'target/*.war'
    cleanWs()
  }
}
}
