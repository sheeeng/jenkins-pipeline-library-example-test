@Library('deadly-viper-library')
import org.contoso.SimpleRandom

pipeline {
    agent any
    stages {
        stage('Abort') {
            when {
                anyOf {  // change `anyOf` to `not` to negate the condition
                    branch 'master'
                    branch 'develop'
                    branch 'release-*'
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
                try {
                    getBuildCauses()
                    sh 'env | sort'
                    // https://issues.jenkins-ci.org/browse/JENKINS-46285
                    sh "echo ${env.BUILD_URL}"
                    sh "echo ${env.BUILD_NUMBER}"
                    sh "echo ${env.GIT_COMMIT}"
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
