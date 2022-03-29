import jenkins.model.Jenkins;
import java.text.SimpleDateFormat;
import java.nio.file.Files;
import java.nio.file.StandardOpenOption;

def simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd");
def simpleDttmFormat = new SimpleDateFormat("yyyy-MM-dd  HH:mm:ss");
def actualNow = new Date();
def now = simpleDttmFormat.format(actualNow);
def group = simpleDateFormat.format(actualNow);

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
                              archiveArtifacts artifacts: '**/dennis.csv', fingerprint: true
                                         }
                                   }
        }
         stage('hihi') {
                      steps {
                      
                      plot csvFileName: 'src/test/jmeter/test.csv', csvSeries: [[displayTableFlag: true, exclusionValues: 'downloads,uploads', file: 'src/test/jmeter/test.csv', inclusionFlag: 'OFF', url: '']], group: "${group}", style: 'line', title: "speedtest", yaxis: 'mbps', useDescr: true

                      
                      
                      
                      
         
            
           
                     }}       
                         
    }
    }





