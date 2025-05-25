pipeline {
    agent any
    stages {
        stage('scm checkout') {

            steps {
                git branch: 'master', url: 'https://github.com/shivrajshinde/maven-project.git'
            }

        }
        stage('code build')
        {
            steps {

                withMaven(
                    globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME',
                    mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn validate'
                }
            }
        }
    }
}
