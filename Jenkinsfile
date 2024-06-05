pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'dockerhub_credentials'
        DOCKER_REPO = 'ghulammohiuddin'
    }

    stages {
      

        stage('i211130 Build and Push Docker Images') {
            parallel {
                stage('i211130 Build and Push Auth Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/auth", './Auth')
                            docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                                app.push("latest")
                            }
                        }
                    }
                }

                stage('i211130 Build and Push Classrooms Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/classrooms", './Classrooms')
                            docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                                app.push("latest")
                            }
                        }
                    }
                }

                stage('i211130 Build and Push Client Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/client", './client')
                            docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                                app.push("latest")
                            }
                        }
                    }
                }

                stage('i211130 Build and Push Event-Bus Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/event-bus", './event-bus')
                            docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                                app.push("latest")
                            }
                        }
                    }
                }

                stage('i211130 Build and Push Post Image') {
                    steps {
                        script {
                            def app = docker.build("${DOCKER_REPO}/post", './Post')
                            docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                                app.push("latest")
                            }
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
