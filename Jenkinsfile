pipeline {
  agent {
    node {
     label 'workstation'
    }
  }
  options {
   ansiColor('xterm')
  }

  triggers { pollSCM('H/2 * * * *') }

  parameters {
         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
         }

  environment {
   TEST_URL="srikaanth.com"
  }
   stages {

     stage ('one') {
      input {
                    message "Should we continue?"
                      ok "Yes"
                  }
     steps {
     sh 'echo hello world'
     sh 'echo ${TEST_URL}'
     sh 'echo person - ${PERSON}'

     }
     }
     stage ('two') {
      when {
      expression {
       GIT_BRANCH == 'origin/main'
      }

      }
     steps {
       sh 'env'
     }

     }
     }

     }
   post {
    always {
      sh 'echo Post CleanUP steps'
    }
   }
