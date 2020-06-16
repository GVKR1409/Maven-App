pipeline {
  agent any
  stages {
    stage('Tool') {
      steps {
        tool(name: 'jdk-1.8.121', type: 'jdk')
        tool(name: 'ant-1.9.8', type: 'ant')
      }
    }

    stage('With Ant') {
      steps {
        withAnt(installation: 'ant-1.9.8', jdk: 'jdk-1.8.121')
      }
    }

    stage('Time') {
      steps {
        timestamps()
      }
    }

    stage('Mail') {
      steps {
        mail(subject: 'Status', body: 'Hello', to: 'vinodkumarreddy.355@gmail.com', from: 'gvkr@gmail.com', cc: 'vinod@gmail.com', bcc: 'sc@gmail.com')
      }
    }

    stage('Test-file-exist-or-not') {
      steps {
        fileExists 'creds'
      }
    }

    stage('Interactive input') {
      steps {
        input(id: 'string', message: 'Enter var1 value', submitterParameter: 'String', submitter: 'vinod')
      }
    }

    stage('Downstream') {
      steps {
        build(job: 'test-gvkr', quietPeriod: 6, wait: true, propagate: true)
      }
    }

    stage('Clone') {
      steps {
        git(url: 'ssh://git@github.com:GVKR1409/Test-jenkins-pipeline.git', branch: 'master', credentialsId: 'test', poll: true)
      }
    }

  }
}