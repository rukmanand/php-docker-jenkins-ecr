node {
  stage("SCM Checkout") {
    git 'https://github.com/rukmanand/php-docker-jenkins-ecr.git'
  }
  stage("Docker Build") {
    docker.build('jenkins-one-ecr')  
  }
  stage("Docker Push to ECR") {
    //docker.withRegistry('https://ap-south-1.console.aws.amazon.com/ecs/home?region=ap-south-1#/repositories/jenkins-one-ecr#images;tagStatus=ALL', 'ecr:ap-south-1:demo-ecr-credentials'){
      //docker.image('jenkins-one-ecr').push('latest')
    //}
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'demo-ecr-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      docker.image('ecs-r/jenkins-one-ecr').push('latestbulidtoecr')
    }

  }
}
