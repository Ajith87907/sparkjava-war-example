pipeline { 
  agent any 
  tools {
    maven 'maven-3.8'
  }
    stages { 
       stage("git_checkout") { 
           steps { 
              echo "cloning repository"
              git 'https://github.com/Ajith87907/sparkjava-war-example.git' 
              echo "repo cloned successfully" 
              } 
         } 
        stage("building_code") { 
           steps { 
              sh 'mvn clean package' 
          } 
      } 
    }
}
