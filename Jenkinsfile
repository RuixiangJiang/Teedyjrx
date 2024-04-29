pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('test'){
            steps{
                sh 'mvn pmd:pmd'
                sh 'mvn test --fail-never'
                sh 'mvn javadoc:jar --fail-never'
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
        }
    }
}