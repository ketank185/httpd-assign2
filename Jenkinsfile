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
				stage ("on slave2") {
					agent {
						label {
							label "slave2"
						}
					}
					steps {
						cleanWs ()
						checkout scm 
						sh "sudo docker run -itdp 84:80 --name httpd-12 httpd"
						sh "sudo docker cp $WORKSPACE/index.html httpd-12:/usr/local/apache2/htdocs/"
					}
				}
			}
}
