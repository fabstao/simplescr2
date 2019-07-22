pipeline {
  agent none
  stages {
    
    stage('Clear_Test 1') {
      agent {
      node 'clrvm'
    }
      steps {
          sh '''#!/bin/bash
echo "test 1"
hostname
echo "test 1"
cat /etc/os-release
sleep 3
uname -a'''
      }
    }
     stage('Clear_Test 2') {
       agent {
      node 'clrvm'
    }
      steps {
          sh '''#!/bin/bash
echo "test 2"
hostname
cat /etc/os-release
sleep 3
uname -a'''
      }
    }
  }
}
