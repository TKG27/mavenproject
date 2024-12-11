pipeline
{
agent none
stages
{
 stage('scm checkout')
 { agent { label 'JAVA'}
  steps { git branch: 'master', url: 'https://github.com/TKG27/mavenproject' }}

 stage('code compile')
 { agent { label 'JAVA'}
  steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true)  {
	sh 'mvn compile'
 } }}

  stage('execute unit test framework')
 { agent { label 'JAVA'}
  steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true)  {
	sh 'mvn test'
 } }}

   stage('code build')
 { agent { label 'JAVA'}
  steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true)  {
	sh 'mvn clean -B -DskipTests package'
 } }}

 //  stage('deploy to tomcat')
// { agent { label: 'JAVA'}
//  steps { sshagent(['DEVCICD']) {
 //   sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@43.204.229.147:/usr/share/tomcat/webapps'
//}
// }}

}
}
