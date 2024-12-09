pipeline
{
agent any
stages
{
 stage('scm checkout')
 { steps { git branch: 'master', url: 'https://github.com/TKG27/mavenproject' }}

 stage('code compile')
 { steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true)  {
	sh 'mvn compile'
 } }}

  stage('execute unit test framework')
 {steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true)  {
	sh 'mvn test'
 } }}

   stage('code build')
 {steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true)  {
	sh 'mvn clean package'
 } }}


}
}
