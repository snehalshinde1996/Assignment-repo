pipeline {
agent any
stages {
   stage ("cleaning workspace")
{
  steps{
  cleanWs()
 }
}
  stage ("checkout from SCM") 
  {
    steps {
     checkout scm
    }
  }
 stage ("creating docker on jenkins master")
	{
	steps
{
  sh """sudo docker run -itdp 80:80 --name httpd-1 httpd"
   sudo docker run -itdp 81:80 --name httpd-2 httpd"
   sudo docker run -itdp 82:80 --name httpd-3 httpd"
 """
  }
}
     stage ("copying index file")
{
	steps
{
	sh """sudo docker cp $WORKSPACE/index.html httpd-1:/usr/local/apche2/htdocs
	 sudo docker cp $WORKSPACE/index1.html httpd-2:/usr/local/apche2/htdocs
	 sudo docker cp $WORKSPACE/index2.html httpd-3:/usr/local/apche2/htdocs
	 """
	}
}

}
}	

