pipeline {
    agent any
	tools {
    	maven 'Maven_Home'
        jdk 'JDK_11'
	}
    stages {
        stage('Initialize Git POLL SCM Feature') {
            steps {
                //Enable remote triggers
                script {
                    properties([[$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.com/bipin115/CICD-deployment-using-Ansible-CM-tool.git'], pipelineTriggers([pollSCM('* * * * *')])])
                }  
            }
        }

	stage('Git project checkout') {
        steps {
               git branch: 'master', url: 'https://github.com/bipin115/CICD-deployment-using-Ansible-CM-tool.git'  
          }
        }
        
        stage(' Applying Playbook to Configurig tomcat server on remote server'){
            steps {
                sh "ansible-playbook tomcat-setup.yaml"
            }
        }
    }
}
