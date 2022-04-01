

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
                sh 'mvn verify'
            }
                  post {
                         always {
                              archiveArtifacts artifacts: '**/test.csv', fingerprint: true
                                         }
                                   }
        }
        stage('Publish JMeter Report') {
                             steps {
                                 publishHTML target: [
                                     allowMissing: false,
                                     alwaysLinkToLastBuild: true,
                                     keepAll: false,
                                     reportDir: 'src/test/jmeter',
                                     reportFiles: 'index.html',
                                     reportName: 'JMeter Report',
                                     reportTitles: 'The Report File Titles'
                                 ]
                             }
                         }
    }
    }





