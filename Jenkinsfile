pipeline {
    agent any

    stages {
        stage('cloning git repository') {
            steps {
                git branch: 'main', url: 'https://github.com/SimeonAkinnuoye/jk-public-gh5.git'
            }
        }
        
        stage('building image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('deploy application') {
            steps {
                sh 'docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}'
            }
        }
    }
}
