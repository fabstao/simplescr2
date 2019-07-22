pipeline {
  agent none
  stages {
    agent {
      node 'clrvm'
    }
    stage('Clear_Test 1') {
      steps {
          sh '''#!/bin/bash
hostname
echo "test 1"
cat /etc/os-release
sleep 3
uname -a'''
      }
    }
     stage('Clear_Test 2') {
      steps {
          sh '''#!/bin/bash
echo "test 2"
cat /etc/os-release
sleep 3
uname -a'''
      }
    }
  }
}
