pipeline {
  agent{
    docker {
      image "node:8-alpine"
      args "--network=skynet"
    }
  }
  stages{
    stage("build"){
      steps{
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/main' >> /etc/apk/repositories"
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/community' >> /etc/apk/repositories"
        sh "apk update"
        sh "apk add --no-cache mongodb yaml-cpp=0.6.2-r2"
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
