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
sleep 2
uname -a'''
      }
    }
     stage('Clear_Test 2') {
      def slaveCIP = InetAddress.localHost.hostAddress
      println "Agent located at ${slaveCIP}"
      steps {
          
          sh '''#!/bin/bash
echo "test 2"
hostname
cat /etc/os-release
sleep 2
uname -a'''
          sh "echo ${slaveCIP}"
      }
    }
    stage('Ubuntu_Test 1') {
       agent {
      node 'ubuntuvm'
    }
      def slaveUIP = InetAddress.localHost.hostAddress
      println "Agent located at ${slaveUIP}"
      steps {
          
          sh '''#!/bin/bash
echo "test UBUNTU 1"
hostname
cat /etc/os-release
sleep 2
uname -a'''
          sh "echo ${slaveUIP}"
      }
    }
  }
}
