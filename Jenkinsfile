pipeline {
  agent{
    docker {
      image "node:8-alpine"
    }
  }
  stages{
    stage("build"){
      steps{
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/main' >> /etc/apk/repositories"
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/community' >> /etc/apk/repositories"
        sh "apk update"
        sh "apk add --no-cache mongodb"
        sh "chmod +x ./scripts/dropdb.sh"
        sh "npm install"
      }
    }
    stage("test"){
      steps{
        sh "npm run test:ci"
      }
    }
  }
}
