podTemplate(containers: [
  containerTemplate(name: 'shell', image: 'alpine:3.14', command: 'sleep', args: '99d'),
]) {

  node(POD_LABEL) {
    stage('stage1') {
      container('shell') {
        sh 'hostname'
        sh 'cat /etc/os-release'
      }
    }
  }
}
