node {
    def mvnHome = tool name: 'maven-3.6.1', type: 'maven'
   stage('checkout the code'){
       git branch: 'development', credentialsId: '0ab39a5a-119c-4cbe-8a0d-3960fe66cfaf', url: 'https://github.com/mallanagouda4/maven-web-application.git'
   }
   
   stage('Build')
   {
       if(isUnix()){
           
           sh "${mvnHome}/bin/mvn deploy sonar:sonar"
       }
       else
       {
           bat "${mvnHome}/bin/mvn deploy sonar:sonar"
       }
   }
   
    stage('deploytomcat')
   {
       if(isUnix()){
           
           sshagent(['pemfile']) {
               
               sh "scp -o StrictHostKeyChecking=no  target/*.war ec2-user@13.233.194.142:/opt/apache-tomcat-9.0.21/webapps/"
    // some block
                                }
    }
    else{
    
    bat 'echo windows'
    }
}
}

    
