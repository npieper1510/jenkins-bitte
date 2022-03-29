

    pipeline {
        agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
        
    stages {
    stage('Remove target') {
                steps {
                    sh 'rm -rf target'
                }
        
            }
            
        stage('build') {
            steps {
                sh 'mvn -Dtest.users=50 -Dtest.tiff=true verify'
            }
             post {
                 always {
                      archiveArtifacts artifacts: '**/dennis.csv', fingerprint: true
                                 }
                           }
        }
                 stage('Publish JMeter Report') {
                     steps {
                         publishHTML target: [
                             allowMissing: false,
                             alwaysLinkToLastBuild: true,
                             keepAll: false,
                             reportDir: 'target/jmeter/reports/testniklas',
                             reportFiles: 'index.html',
                             reportName: 'JMeter Report',
                             reportTitles: 'The Report File Titles'
                         ]
                     }
                 }
                            
                         
    }
    }



