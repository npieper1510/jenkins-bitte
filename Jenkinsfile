

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
         stage('Generate Cucumber Report') {
                                steps {
                                    perfReport 'target/jmeter/reports/test555/index.html'
                                }
                            }
                            
                         
    }
    }



