pipeline {
    agent any

    environment {
        DOCKER_REPO = 'ghulammohiuddin'
    }

    stages {
       

        stage('i211130 Build Docker Images') {
            parallel {
                stage('i211130 Build Auth Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/auth", './Auth')
                        }
                    }
                }

                stage('i211130 Build Classrooms Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/classrooms", './Classrooms')
                        }
                    }
                }

                stage('i211130 Build Client Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/client", './client')
                        }
                    }
                }

                stage('i211130 Build Event-Bus Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/event-bus", './event-bus')
                        }
                    }
                }

                stage('i211130 Build Post Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/post", './Post')
                        }
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
