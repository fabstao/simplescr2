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
cat /etc/os-release
uname -a'''
          script {
              def slaveCIP = InetAddress.localHost.canonicalHostName
              println "Agent located at ${slaveCIP}"
              echo "Agente: ${slaveCIP}"
              def myip = "ip a | awk '/inet6|127/ {next;} /inet/ {print \$2}' | sed 's/\/[0-9][0-9]//g'".execute().text
              echo "Agente: ${myip}"
        }
        
     }
    }
     stage('Clear_Test 2') {
      
      steps {
          
          sh '''#!/bin/bash
echo "test 2"
hostname
cat /etc/os-release
sleep 2
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
sleep 2
uname -a'''
          script {
              def myip = "ip a | awk '/inet6|127/ {next;} /inet/ {print \$2}' | sed 's/\/[0-9][0-9]//g'".execute().text
              echo "Agente: ${myip}"
              def nodes = 1
              for (int i = 0; i < nodes; ++i) {
                  echo "Testing the ${i} node ${slaveUIP}"
                 }
          }
        }
      }
    }
  }
