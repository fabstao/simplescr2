pipeline {
  agent {
      node 'clrvm'
    }
  stages {
    
    stage('Clear_Test 1') {
      
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
      steps {
          sh '''#!/bin/bash
echo "test 2"
hostname
cat /etc/os-release
sleep 3
uname -a'''
      }
    }
    stage('Ubuntu_Test 1') {
       agent {
      node 'ubuntuvm'
    }
      steps {
          sh '''#!/bin/bash
echo "test UBUNTU 1"
hostname
cat /etc/os-release
sleep 3
uname -a'''
      }
    }
  }
}
