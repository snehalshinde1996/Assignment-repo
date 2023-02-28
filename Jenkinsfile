pipeline {
	agent any
 stages {
	stage ("cleaning workspace")
	{
	 steps{
	 cleanWs()
	 }
    }
    stage ("cloning git"){
    steps {
     checkout scm
    }
    }
	stage ("creating docker on jenkins master")
	{
	steps{
  sh "sudo docker run -itdp 80:80 --name httpd-1 httpd"
  sh "sudo docker run -itdp 80:81 --name httpd-2 httpd"
  sh "sudo docker run -itdp 80:82 --name httpd-3 httpd"

  }
	}
stage (copying index file)
{
	steps{
	sh "sudo docker cp $Woskspace/index.html httpd-1:/usr/local/apche2/htdocs"
	sh "sudo docker cp $Woskspace/index1.html httpd-2:/usr/local/apche2/htdocs"
	sh "sudo docker cp $Woskspace/index2.html httpd-3:/usr/local/apche2/htdocs"
	}
}

	}
	
}
