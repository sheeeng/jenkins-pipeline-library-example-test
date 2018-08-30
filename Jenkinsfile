@Library('deadly-viper-library')
import org.contoso.SimpleRandom

node {
    stage('Abort') {
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
