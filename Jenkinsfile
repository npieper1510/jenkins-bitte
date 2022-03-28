pipeline {
    agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn verify'
            }
             post {
                 always {
                      archiveArtifacts artifacts: '**/*.csv', fingerprint: true
                                 }
                           }
        }
         stage('Generate Cucumber Report') {
                                steps {
                                    perfReport 'target/jmeter/results/20220324-test.csv'
                                }
                            }
    }
}
