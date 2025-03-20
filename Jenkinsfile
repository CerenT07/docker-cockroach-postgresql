pipeline {
    agent any

    environment {
        // Docker Compose komut dosyasının yolu Windows'a uygun şekilde belirlenmeli
        DOCKER_COMPOSE = "C:\\Users\\HP\\docker-cockroach-postgresql\\docker-compose.yml"  // Docker Compose'un yolu
    }

    stages {
        stage('Checkout') {
            steps {
                // GitHub'dan proje çekme
                git 'https://github.com/CerenT07/docker-cockroach-postgresql.git'
            }
        }

        stage('Start Containers') {
            steps {
                script {
                    // Docker Compose ile container'ı başlat
                    bat "\"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker-compose.exe\" -f \"${DOCKER_COMPOSE}\" up -d"
                }
            }
        }

        stage('Verify Containers') {
            steps {
                script {
                    // Docker konteynerlerinin çalışıp çalışmadığını kontrol et
                    bat "docker ps"
                }
            }
        }

        stage('Stop Containers') {
            steps {
                script {
                    // Docker Compose ile konteynerları durdur
                    bat "\"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker-compose.exe\" -f \"${DOCKER_COMPOSE}\" down"
                }
            }
        }
    }
}
