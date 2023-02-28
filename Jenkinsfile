pipeline {
		agent slave1
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
					}
				}
			}
}
