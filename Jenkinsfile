pipeline {
    agent any
    GithubUrl = 'https://github.com/woodjooe/Sprng-Devops'
    stages {
        stage('Build ConfigServer') {
            steps {
                // Get code from your GitHub repository and the ConfigServer folder
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GithubUrl + '/springProject.git']]])
                dir('ConfigServer') {
                    // Run Maven on a Unix agent.
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/ConfigServer/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'ConfigServer/target/*.jar'
                }
            }
        }
        
        stage('Build and Push Docker Image ConfigServer') {
            steps {
                dir('ConfigServer') {
                    // Build Docker image
                    script {
                        sh 'docker build -t ' + GithubUrl + ':config-server-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         sh 'docker login -u woodjooe -p ******'
                         sh 'docker push woodjooe/Sprng-Devops:config-server-latest'
                          // Run a command inside the Docker container
                       
                        sh 'docker run -d --net host woodjooe/Sprng-Devops:config-server-latest'
                    }
                }
            }
        
        }
        stage('Build registryService') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GithubUrl + '/springProject.git' ]]])
                 dir('registryService') {
            sh "mvn clean package -DskipTests"
            }
        }

    post {
        success {
            archiveArtifacts 'registryService/target/*.jar'
        }
            }
        }
        stage('Build and Push Docker Image registryService') {
            steps {
                dir('registryService') {
                    // Build Docker image
                    script {
                        sh 'docker build -t woodjooe/Sprng-Devops:registry-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push woodjooe/Sprng-Devops:registry-service-latest'
                         sh 'docker run -d woodjooe/Sprng-Devops:registry-service-latest'
                    }
                }
            }
        
        }
        stage('Build Gateway-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GithubUrl + '/springProject.git']]])
                dir('Gateway-service') {
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
            }

            post {
                success {
                    junit '**/Gateway-service/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'Gateway-service/target/*.jar'
                }
            }
        }
        stage('Build and Push Docker Image Gateway-service') {
            steps {
                dir('Gateway-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t woodjooe/Sprng-Devops:gateway-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                       
                         sh 'docker push woodjooe/Sprng-Devops:gateway-service-latest'
                         sh 'docker run -d woodjooe/Sprng-Devops:gateway-service-latest'
                    }
                }
            }
        
        }
        stage('Build Evenement-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GithubUrl + '/springProject.git']]])
                dir('Evenement-service') {
                    sh "mvn clean package -DskipTests"
                }
            }

            post {
                success {
                    
                    archiveArtifacts 'Evenement-service/target/*.jar'
                }
            }
        }
        stage('Build and Push Docker Image Evenement-service') {
            steps {
                dir('Evenement-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t woodjooe/Sprng-Devops:evenement-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push woodjooe/Sprng-Devops:evenement-service-latest'
                         sh 'docker run -d woodjooe/Sprng-Devops:evenement-service-latest'
                    }
                }
            }
        
        }
        stage('Build Outil-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GithubUrl + '/springProject.git']]])
                dir('Outil-service') {
                    sh "mvn clean package -DskipTests"
                }
            }

            post {
                success {
                    
                    archiveArtifacts 'Outil-service/target/*.jar'
                }
            }
        }
        stage('Build and Push Docker Image Outil-service') {
            steps {
                dir('Outil-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t woodjooe/Sprng-Devops:outil-service-latest .'
                        
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push woodjooe/Sprng-Devops:outil-service-latest'
                         sh 'docker run -d woodjooe/Sprng-Devops:outil-service-latest'
                    }
                }
            }
        
        }
        stage('Build Publication-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GithubUrl + '/springProject.git']]])
                dir('Publication-service') {
                    sh "mvn clean package -DskipTests"
                }
            }

            post {
                success {
                    
                    archiveArtifacts 'Publication-service/target/*.jar'
                }
            }
        }
        stage('Build and Push Docker Image Publication-service') {
            steps {
                dir('Publication-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t woodjooe/Sprng-Devops:publication-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push woodjooe/Sprng-Devops:publication-service-latest'
                         sh 'docker run -d woodjooe/Sprng-Devops:publication-service-latest'
                    }
                }
            }
        
        }
        stage('Build Membre-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GithubUrl + '/springProject.git']]])
                dir('Membre-service') {
                    sh "mvn clean package -DskipTests"
                }
            }

            post {
                success {
                    
                    archiveArtifacts 'Membre-service/target/*.jar'
                }
            }
        }
        stage('Build and Push Docker Image Membre-service') {
            steps {
                dir('Membre-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t woodjooe/Sprng-Devops:membre-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push woodjooe/Sprng-Devops:membre-service-latest'
                         sh 'docker run -d woodjooe/Sprng-Devops:membre-service-latest'
                    }
                }
            }
        
        }
    }
}
