pipeline {
  agent none
  stages {
    stage('Clear_Test') {
      steps {
        node('clrvm') {
          sh '''#!/bin/bash
hostname
cat /etc/os-release
sleep 3
uname -a'''
        }
        node('ubuntuvm'){
          sh '''#!/bin/bash
hostname
cat /etc/os-release
sleep 5
uname -a'''
             }
      }
    }
  }
}
