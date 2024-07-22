pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/vanessatan157/JenkinsDependencyCheckTest.git', branch: 'master'
            }
        }

        stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                dependencyCheck additionalArguments: '''
                    -o './'
                    -s './'
                    -f 'ALL'
                    --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities',

                // Just add this line, based on what you set on ID,
                // the rest is based on the Medium post on Lab6
                nvdCredentialsId: 'd8ad5e54-6369-4418-8485-fba9d7da3d71 ' 

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