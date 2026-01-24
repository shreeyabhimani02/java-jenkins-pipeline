pipeline {
agent any
environment {
// Set JAVA_HOME to the path of your Java 17 installation
JAVA_HOME = 'C:\\Program Files\\Java\\jdk-17'
// Add Java bin directory to PATH
PATH = "${JAVA_HOME}\\bin;${env.PATH}"
}
tools {
maven 'maven3'
}
stages {
stage('GetCode') {
steps {
git branch: 'main', url: 'https://github.com/mgidw/test.git'
}
}
stage('SonarQube analysis') {
steps {
withSonarQubeEnv('SonarQubeserver') {
bat script: """
sonar-scanner -D"sonar.projectKey=devops" \
-D"sonar.sources=." \
-D"sonar.host.url=http://localhost:9000" \
-D"sonar.login=sqa_0d747851b94e00b6005b1acdcaed8a0a82b6fc64"
"""
}
}
}
}
}
