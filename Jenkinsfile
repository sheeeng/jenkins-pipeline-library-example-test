//https://stackoverflow.com/a/48421660/4763512
def jobs = ["JobA", "JobB", "JobC"]

def parallelStagesMap = jobs.collectEntries {
    ["${it}" : generateStage(it)]
}

def generateStage(job) {
    return {
        stage("stage: ${job}") {
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
        stage('Sequential') {
            steps {
                echo 'Message from the declarative non-parallel stage.'
            }
        }

        stage('Parallel') {
            steps {
                script {
                    parallel parallelStagesMap
                }
            }
        }
    }
}
