def jobs = ["JobA", "JobB", "JobC"]

def parallelStagesMap = jobs.collectEntries {
    ["${it}": generateStage(it)]
}

def generateStage(job) {
    return {
        stage("Parallel Sub-Stage: ${job}") {
            node("${job}") {
                echo "Message from the generated ${job} scripted parallel stage."
                sh script: "sleep 8"
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Parallel: Declarative') {
            failFast true
            parallel {
                stage('Windows') {
                    steps {
                        sh 'echo Message from Windows stage.'
                    }
                }
                stage('Ubuntu') {
                    steps {
                        sh 'echo Message from Ubuntu stage.'
                    }
                }
            }
        }

        stage('Parallel: Scripted') {
            failFast true
            steps {
                script {
                    parallel parallelStagesMap
                }
            }
        }
    }

    post {
        always {
            deleteDir()
        }
    }
}
