pipeline {
    agent { label "OPEN"}
    stages {
        stage ("vcs") {
            steps {
                git url: "https://github.com/ansible/ansible.git",
                branch: "devel"
            }
        }
        stage ("python_run") {
            steps {
                sh "python3 -m pip install -U -r requirements.txt"
            }
        }
		stage ("python_install") {
            steps {
                sh "sudo python3 setup.py install"
            }
        }
		stage("show_version") {
            steps {
              sh "ansible --version"
            }
		}
        stage ("version") {
            steps {
                dir("ansible") {
                   sh "sudo tox run"
                }
            }
        }
    }
}
