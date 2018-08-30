@Library('deadly-viper-library')
import org.contoso.SimpleRandom

pipeline {
    agent any
    stages {
        stage('Abort') {
            when {  // https://jenkins.io/doc/book/pipeline/syntax/#when
                beforeAgent true
                anyOf {  // Nested when condition "not" requires exactly 1 child condition.
                    branch 'master'  // Note that this only works on a multibranch Pipeline. ¯\_(ツ)_/¯
                    environment name: 'ABORT_PREVIOUS_BUILDS', value: 'true'
                }
            }
            steps {
                println "Aborting previous builds if exists."
                abortPreviousBuilds()
            }
        }
        stage('Main') {
            steps {
                println env.GIT_BRANCH
                getBuildCauses()
                sh 'env | sort'
                // https://issues.jenkins-ci.org/browse/JENKINS-46285
                println '\${BUILD_NUMBER}:'
                sh "echo ${env.BUILD_NUMBER}"
                println '\${GIT_BRANCH}:'
                sh "echo ${env.GIT_BRANCH}"
                println '\${GIT_COMMIT}:'
                sh "echo ${env.GIT_COMMIT}"
                println '\${GIT_PREVIOUS_COMMIT}:'
                sh "echo ${env.GIT_PREVIOUS_COMMIT}"
                println '\${GIT_PREVIOUS_SUCCESSFUL_COMMIT}:'
                sh "echo ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}"
                sleep 42
            }
        }
    }
}
