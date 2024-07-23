pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/vanessatan157/JenkinsDependencyCheckTest', branch: 'master'
            }
        }
        stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                dependencyCheck additionalArguments: '''
                    -o ./
                    -s ./
                    -f ALL
                    --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
        
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
    }   
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
