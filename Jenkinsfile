@Library('shared-library@develop') _
def BUILD_TRIGGER_BY
pipeline {
    agent any
    environment {
        // get git commit from Jenkins
        GIT_COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
        DOCKER_NAME = "${JOB_BASE_NAME}/${env.BRANCH_NAME}"
    }
    stages {
        stage('Initial') {
            steps {
                script {
                    BUILD_TRIGGER_BY = currentBuild.getBuildCauses()[0].shortDescription + " / " + currentBuild.getBuildCauses()[0].userId
                }
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:14-alpine'
                }
            }
            steps {
                echo "Building project from branch ${env.BRANCH_NAME} - Commit ${GIT_COMMIT}"
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo "Testing project"
                sh 'npm test -- --coverage'
            }
            post {
                always {
                    publishHTML target: [
                        allowMissing         : false,
                        alwaysLinkToLastBuild: false,
                        keepAll             : true,
                        reportDir            : 'output/coverage/jest',
                        reportFiles          : 'index.html',
                        reportName           : 'Test Report'
                    ]
                }
                success {
                    echo 'SUCCESS'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "Docker image name: ${DOCKER_NAME}"
                echo "Docker image tag: ${GIT_COMMIT}"
                // sh "docker build -t ${DOCKER_NAME}:${GIT_COMMIT} ."
            }
        }
    }
    post {
        always {
            echo "Build final status triggered by ${BUILD_TRIGGER_BY}: ${currentBuild.currentResult}"
        }
        success {
            script {
                email.sendSuccessEmail()
            }
        }
        failure {
            script {
                email.sendFailureEmail("${currentBuild.previousFailedBuild}")
            }
        }
    }
}