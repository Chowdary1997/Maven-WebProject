node{

   def tomcatWeb = 'C:\\Tomcat-8.5.33\\webapps'
   def tomcatBin = 'C:\\Tomcat-8.5.33\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/cubeiplKumar/Maven-WebProject.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\maven-stanalone-application-0.0.1-SNAPSHOT.jar \"${tomcatWeb}\\maven-stanalone-application-0.0.1-SNAPSHOT.jar\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
