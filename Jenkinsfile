pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git 'https://github.com/name54321/JenkinsDependencyCheckTest.git'
            }
        }

        stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                script {
                    def nvdApiKey = 'b5b67dad-17ec-4f1f-8814-51bb72c2f93b'

                    // Run Dependency-Check with additional arguments including API key
                    sh '''
                        dependency-check.sh
                        --format HTML --format XML
                        --nvd-api-key ${nvdApiKey}
                    '''
                }
            }
        }
    }
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
