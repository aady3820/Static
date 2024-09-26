node {
  checkout scm;
  def webDirectory = '/var/www/html'
  stage('Install nginx') {
       echo 'check if Nginx is installed'
    def nginxInstalled = sh(script:'which nginx',return status: true) == 0
  if(!nginxInstalled)
     echo 'Nginx not found. Installing nginx'
    sh '''
    sudo apt-get update
    sudo apt-get install -y nginx
    '''
  } else {
    echo 'Nginx is Installed'
  }
}
 stage('Deployment of Website'){
   sh '''
   sudo cp -r * ${webDirectory}/
   '''
   echo 'Website Deployed'
 }
stage('Restart Nginx'){
  sh 'sudo systemctl restart nginx'
}

