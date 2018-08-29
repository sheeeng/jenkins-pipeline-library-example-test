@Library('deadly-viper-library')
import org.contoso.WesterosFolks

//https://stackoverflow.com/a/48421660/4763512
def jobs = ["JobA", "JobB", "JobC"]

def parallelStagesMap = jobs.collectEntries {
    ["${it}" : generateStage(it)]
}

def generateStage(job) {
    return {
        stage("stage: ${job}") {
            echo "\044\{job\}: ${job}."
            sh script: "sleep 8"
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

        stage('scripted in declarative stage') {
            steps {
                script {
                    node {
                        stage('Main') {
                            try {
                                abortPreviousBuilds()
                                sh 'env | sort'
                                sleep 42
                            }
                            catch (e) {
                                echo 'Uh oh! What happened?'
                                throw e
                            }
                        }
                    }
                }
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


