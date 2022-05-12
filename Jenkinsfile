pipeline { 
  agent any 
    stages { 
       stage (“git checkout”) { 
           steps { 
              echo “cloning repository”	
              git 'https://github.com/Ajith87907/sparkjava-war-example.git' 
              echo “repo cloned successfully” 
              } 
         } 
        stage (“building code”) { 
           steps { 
              sh ’./mvnw clean package’ 
            	sh ‘mv target/*.war target/myweb.war’ 
                 echo “build successful” 
          } 
      } 
       stage (“deploy”) { 
         steps { 
           sshagent([‘tomcat-dev1’]) 
           sh “”” 
           scp –o StringHostKeyChecking=no target/myweb.war 
           ubuntu@yourip:/opt/tomcat/webapps/ 
           ssh ubuntu@yourip /opt/tomcat/bin/startup.sh 
             “”” 
            } 
        } 
    }
}
