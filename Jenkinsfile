pipeline{
   agent any
   stages{
   stage("Git Checkout"){
   steps{
      git credentialsId: '123' , url: 'https://github.com/SaimskIN/Depoy.git'
      }
      }
      stage("Maven build"){
      steps{
      sh "mvn clean package"
      sh "mv target/*.war target/myweb.war
      }
      }
      stage("Deploy"){
      steps{
      sshagent(['tomcat-new']) {
      sh """
      scp -o strictHostkeychecking=no target/myweb.war ec2-user@18.117.178.185:/home/ec2-user/apache-tomcat-9.0.56/webaps/
     
     ssh ec2-user@18.117.178.185/home/ec2-user/apache-tomcat-9.0.56/bin/shutdown.sh
     
     ssh ec2-user@18.117.178.185 /home/ec2-user/apache-tomcat-9.0.56/bin/startup.sh
     
     """
    }
    }
    }
    }
    }
    
