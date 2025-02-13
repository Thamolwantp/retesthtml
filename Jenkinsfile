pipeline {
    agent any
    stages {
        stage("Copy file to Docker server") {
            steps {
                // แก้ตรง team33-neogym ให้เป็นชื่อเดียวกันกับ pipeline job/item ที่สร้างใน jenkins
                sh "scp -r /var/lib/jenkins/workspace/admin-neogym/* root@13.212.94.247:~/admin-neogym"
            }
        }

        stage("Build Docker Image") {
            steps {
                // path yaml files
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/admin-neogym/playbooks/build.yaml'
            }
        }

        stage("Create Docker Container") {
            steps {
                // path yaml files
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/team33-neogym/playbooks/deploy.yaml'
            }
        }
    }
}
