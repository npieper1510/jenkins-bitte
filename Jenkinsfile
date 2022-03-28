def call(cloudConfiguration="cmp-dev", jdkVersion="jdk11") {

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
                                    perfReport 'target/jmeter/results/test.csv'
                                }
                            }
                            
                            stage('get config file') {
                                        sh "wget https://raw.githubusercontent.com/Blazemeter/taurus/master/examples/jmeter/stepping.yml"
                                }
                                
                                stage("run test") {
                                    bzt "stepping.yml"
                                }
    }
}


