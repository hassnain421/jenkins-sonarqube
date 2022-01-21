node {
  stage ('Cloning from Git') {
    git 'https://github.com/hassnain421/jenkins-sonarqube.git'
  }/*
  stage ('Execute Maven') {
    mvnHome = tool 'maven'
    sh 'mvn clean install'
  }*/
 stage ('SonarQube Analysis') {
    def scannerHome = tool 'sonarqube';
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner \
      -D sonar.login=admin \
      -D sonar.password=admin123 \
      -D sonar.projectKey=test \
      -D sonar.sources=/mnt/jenkins-home/workspace/sonarqube/src/main/ \
      -D sonar.tests=/mnt/jenkins-home/workspace/sonarqube/src/test/ \
      -D sonar.host.url=http://192.168.52.128:9000"
    }
  }
}
