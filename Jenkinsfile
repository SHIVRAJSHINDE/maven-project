pipeline {
    agent any
    stages {
        stage('scm checkout') {

            steps {
                git branch: 'master', url: 'https://github.com/shivrajshinde/maven-project.git'
            }

        }

        stage('code validate')
        {
            steps {

                withMaven(
                    globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME',
                    mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn validate'
                }
            }
        }


        stage('code compile')
        {
            steps {

                withMaven(
                    globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME',
                    mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn compile'
                }
            }
        }



        stage('code test')
        {
            steps {

                withMaven(
                    globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME',
                    mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn test'
                }
            }
        }


        stage('code build')
        {
            steps {

                withMaven(
                    globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME',
                    mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn package'
                }
            }
        }


        stage('code deploy')
        {
            steps {

                sshagent(['DEVCICD']) {
                   sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@15.206.128.161:/usr/share/tomcat/webapps/'
                    }

                }
            }
        }

}

