node('master'){
   
   stage('git checkout'){
                  git 'https://github.com/mythribhay/Inglibrary.git'
              }
   
   stage('Static code analysis'){
             sh '/opt/maven/bin/mvn sonar:sonar -Dsonar.password=admin -Dsonar.login=admin'
         }
   stage('java build'){
             sh '/opt/maven/bin/mvn clean install'
         }

   stage('Running java backend application'){
             sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=dev -jar $WORKSPACE/target/*.jar &'
         }
   
   stage('java deploy'){
             sh '/opt/maven/bin/mvn clean deploy '
         }
}

