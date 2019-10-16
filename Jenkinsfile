node('master'){
   stage('git checkout'){
                  git 'https://github.com/ajitesh17/INGPRODUCTS'
      withMaven(
        // Maven installation declared in the Jenkins "Global Tool Configuration"
        maven: 'maven-3',
        // Maven settings.xml file defined with the Jenkins Config File Provider Plugin
        // We recommend to define Maven settings.xml globally at the folder level using
        // navigating to the folder configuration in the section "Pipeline Maven Configuration / Override global Maven configuration"
        // or globally to the entire master navigating to  "Manage Jenkins / Global Tools Configuration"
        mavenSettingsConfig: 'my-maven-settings') {
 
      // Run the maven build
      sh "mvn clean verify"
 
    } // withMaven w
              }
   stage('java build'){
             sh 'mvn clean install sonar:sonar -Dsonar.password=admin -Dsonar.login=admin'
         }
   stage('Running java backend application'){
             sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=dev -jar $WORKSPACE/target/*.jar &'
         }
}
