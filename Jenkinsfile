node('master'){
   
   stage('Git checkout'){
                  git 'https://github.com/mythribhay/Inglibrary.git'
              }
   
   stage('Static code analysis'){
             sh '/opt/maven/bin/mvn clean verify sonar:sonar -Dsonar.password=admin -Dsonar.login=admin'
         }
   stage('Java build'){
             sh '/opt/maven/bin/mvn clean install'
         }

   stage('Running java jar file'){
             sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=dev -jar $WORKSPACE/target/*.jar &'
         }
   
   stage('Java deploy'){
             sh '/opt/maven/bin/mvn clean deploy '
         }
}

