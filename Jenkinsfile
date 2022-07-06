node{

   def tomcatWeb = 'D:\\Auto_deployment\\apache-tomcat-9.0.64\\apache-tomcat-9.0.64\\webapps'
   def tomcatBin = 'D:\\Auto_deployment\\apache-tomcat-9.0.64\\apache-tomcat-9.0.64\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/localmain/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
       sh "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               sh ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.sh"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     sh "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
          sh "${tomcatBin}\\startup.sh"
         sleep(time:100,unit:"SECONDS")
   }
}
