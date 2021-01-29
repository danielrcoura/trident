pipeline {
   agent any
   tools {
        go 'go-1.15.17'
    }
    stages {
        stage('build') {
            steps {
                echo '-0-0-0-0-0-0-0- rodou esta linha! -0-0-0-0-0-0-0-'
            }
        }
        stage('test') {
          steps {
            sh 'curl -sfL https://install.goreleaser.com/github.com/golangci/golangci-lint.sh | bash -s -- -b $(go env GOPATH)/bin v1.35.2'
            sh 'curl -sf https://raw.githubusercontent.com/danielrcoura/jenkins-test/master/main --output $(go env GOPATH)/bin/issues-import'
            sh 'chmod +x $(go env GOPATH)/bin/issues-import'
            sh '$(go env GOPATH)/bin/issues-import'
          }
        }
    }
}
