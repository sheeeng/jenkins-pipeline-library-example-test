//https://stackoverflow.com/a/48421660/4763512
def jobs = ["JobA", "JobB", "JobC"]

def parallelStagesMap = jobs.collectEntries {
    ["${it}" : generateStage(it)]
}

def generateStage(job) {
    return {
        stage("stage: ${job}") {
            node("${job}") {
                echo "Message from the generated ${job} stage."
                sh script: "sleep 8"
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('declarative non-parallel stage') {
            steps {
                echo 'This declarative non-parallel stage will be executed first.'
            }
        }

        stage('scripted in declarative parallel stage') {
            steps {
                script {
                    parallel parallelStagesMap
                }
            }
        }
    }
}
