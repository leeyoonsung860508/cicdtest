pipeline {
  agent any
    stages {
        stage('git scm update') {
	      steps {
	              git url: 'https://github.com/leeyoonsung/jenkinstest.git', branch: 'master'
		            }
			        }
				    stage('docker build and push') {
				          steps {
					          sh '''
						          sudo docker build -t leeyoonsung/testshop:newnewmain .
							          sudo docker push leeyoonsung/testshop:newnewmain								          '''
									        }
										    }
										        stage('deploy k8s') {
											      steps {
											              sh '''
												              sudo export KUBECONFIG=/etc/kubernetes/admin.conf
													      sudo kubectl set image deployment deploy-main ctn-main=leeyoonsung/testshop:newnewmain
													          														              --target-port=80 --name=testpipeline-svc
															              '''
				}		
			}
										  }
 }
