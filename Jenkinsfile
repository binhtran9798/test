properties([pipelineTriggers([upstream(threshold: 'FAILURE', upstreamProjects: 'hello, ')])])
pipeline {  
      agent { label 'master' }
    stages {
//         stage('SCM') {
//             steps {
//                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/binhtran9798/demojenkinspipeline.git']]])
//             }
//         }
        stage('build') {
            steps {
                // withMaven(jdk: 'jdk1.8', maven: 'maven-3.8.1') {
                // bat 'mvn clean install'
                // }
                echo 'this is newbranch1'
            }
        }
    }
     environment {
        EMAIL_TO = 'emaildehoc2019@gmail.com'
    }
post {
        success {
            emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}', 
                    to: "${EMAIL_TO}", 
                    subject: 'Build success in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'
        }
        failure {
            emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}', 
                    to: "${EMAIL_TO}", 
                    subject: 'Build failed in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'
        }
//         unstable {
//             emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}', 
//                     to: "${EMAIL_TO}", 
//                     subject: 'Unstable build in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'
//         }
//         changed {
//             emailext body: 'Check console output at $BUILD_URL to view the results.', 
//                     to: "${EMAIL_TO}", 
//                     subject: 'Jenkins build is back to normal: $PROJECT_NAME - #$BUILD_NUMBER'
//         }
    }
 }
