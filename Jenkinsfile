pipeline {
  agent any
  stages {
        stage(' git clone or git pull' ) {
          steps {
	    git url: 'https://github.com/jadechoi/jenkins_quiz.git', branch: 'master'
	  }
	}

        stage(' docker image build and push to p-registry' ) {
	  steps {
	    sh '''
            docker build -t 192.168.8.100:5000/web:bule .
	    docker push 192.168.8.100:5000/web:blue
	    '''
	  }
	}
	stage(' deployment, svc create ' ) {
          steps {
	    sh '''
	    kubectl apply -f blue.yaml
	    '''
	  }

	}

  }
}
