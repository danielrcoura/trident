pipeline {
   agent any
   tools {
        go 'go-1.15.17'
    }
    stages {
        stage('build') {
            steps {
                echo '----- building... -----'
                sh 'go build'
            }
        }
        stage('code analysis') {
          steps {
            echo '----- code analysis... -----'
            sh 'curl -sfL https://install.goreleaser.com/github.com/golangci/golangci-lint.sh | bash -s -- -b $(go env GOPATH)/bin v1.35.2'
            sh 'curl -sf https://raw.githubusercontent.com/danielrcoura/jenkins-test/master/main --output $(go env GOPATH)/bin/issues-import'
            sh 'chmod +x $(go env GOPATH)/bin/issues-import'
            sh '$(go env GOPATH)/bin/issues-import'
          }
        }
    }
}
