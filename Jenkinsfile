

    pipeline {
        agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
        
    parameters {
              booleanParam(name: 'SHOULD_DELETE', defaultValue: false, description: 'Gibt an ob die Datenbank aufgeräumt werden soll')
                choice(name: 'TARGET_ENVIRONMENT', choices: ['dev', 'test'], description: 'Umgebung auf der getestet werden soll')
    }
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
                              archiveArtifacts artifacts: '**/load-test-report.csv', fingerprint: true
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
                                     reportFiles: 'csv.html',
                                     reportName: 'JMeter Report',
                                     reportTitles: 'The Report File Titles'
                                 ]
                             }
                         }
    }
    }





