podTemplate(containers: [
  containerTemplate(name: 'shell', image: 'alpine:3.14', command: 'sleep', args: '99d'),
  containerTemplate(name: 'kaniko', image: 'gcr.io/kaniko-project/executor:latest', command: '/busybox/cat', ttyEnabled: true)
]) {

  node(POD_LABEL) {
    stage('Git') {
      checkout scm
    }
    stage('Build') {
      container('kaniko') {
        sh '/kaniko/executor -f `pwd`/Dockerfile -c `pwd` --cache=true --destination=nginx-myhello:latest'
      }
      
    }
    stage('stage1') {
      container('shell') {
        sh 'hostname'
        sh 'cat /etc/os-release'
      }
    }
  }
}
