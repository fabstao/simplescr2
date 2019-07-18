pipeline {
  agent none
  stages {
    stage('Clear_Test') {
      steps {
        node('clrvm') {
          sh '''#!/bin/bash
hostname
lscpu
sleep 3
uname -a'''
        }
        node('ubuntuvm'){
          sh '''#!/bin/bash
hostname
lscpu
sleep 15
uname -a'''
             }
      }
    }
  }
}
