

    pipeline {
        agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
        
    stages {
        stage('build') {
            steps {
                sh 'mvn -Dtest.users=50 -Dtest.tiff=true verify'
            }
             post {
                 always {
                      archiveArtifacts artifacts: '**/*.csv', fingerprint: true
                                 }
                           }
        }
                 stage('Publish JMeter Report') {
                     steps {
                         publishHTML target: [
                             allowMissing: false,
                             alwaysLinkToLastBuild: true,
                             keepAll: false,
                             reportDir: 'target/jmeter/reports/test555',
                             reportFiles: 'index.html',
                             reportName: 'JMeter Report',
                             reportTitles: 'The Report File Titles'
                         ]
                     }
                 }
                            
                         
    }
    }



