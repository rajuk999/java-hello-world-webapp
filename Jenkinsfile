pipeline{
     agent any 
     tools {
         maven 'Maven'
         
     }
     
     stages{
         
         stage ('Initialize') {
             steps {
                     sh '''
                         echo "PATH = ${PATH}"
                         echo "M2_HOME = ${M2_HOME}"
                     '''
                 }
             }
         stage('checkout stage'){
             steps{
                 git credentialsId: '8b4d5611-418f-48f0-a831-02baf2b87c75', url: 'https://github.com/rajuk999/java-hello-world-webapp.git'           
}
}
         stage('Build-stage'){
             steps{
                 sh 'mvn clean package'
                 sh 'mv target/*.war target/demo.war'
}
}
         stage('deploy war file'){
             steps{
                 sshagent(['ec2-id']) {
                 sh "scp -o StrictHostKeyChecking=no target/demo.war ubuntu@172.31.5.153:/opt/tomcat/webapps"
                             }
                         }
                     }
}
}
