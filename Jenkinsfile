pipeline {
    
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('checkout') {
            
            steps {
                git url: 'https://github.com/sumanthtalasila/moc.git',branch:'main'
               
            }
        }

        stage('build') {
            steps {
                 bat 'mvn clean package'
            }
            post {
                success {
                    junit 'target/surefire-reports/TEST-*.xml'
                    archiveArtifacts artifacts: 'target/moc-*.jar', followSymlinks: false
                }
            }
        }
    }
}