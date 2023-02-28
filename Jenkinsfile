pipeline {
		agent {
			label {
				label "slave1"
				  }
			  }
			stages {
				stage ("cleaning workspace") {
					steps {
						cleanWs ()
					}
				}
				stage ("checkout code from scm") {
					steps {
						checkout scm
					}
				}
				stage ("creating container on slave1") {
					steps {
						sh "docker run -itdp 83:80 --name httpd-11 httpd"
						sh "docker cp $WORKSPACE/index.html httpd-11:/usr/local/apache2/htdocs/"	
						}
				}
			}
}
