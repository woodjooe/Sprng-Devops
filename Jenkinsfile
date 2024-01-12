def GithubUrl = 'https://github.com/woodjooe/Sprng-Devops'

pipeline {
    agent any
    stages {
        stage('Build ConfigServer') {
            steps {
                // Get code from your GitHub repository and the ConfigServer folder
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/woodjooe/Sprng-Devops.git']]])
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
        stage('Build registryService') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url:'https://github.com/woodjooe/Sprng-Devops.git' ]]])
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


        stage('Build Gateway-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/woodjooe/Sprng-Devops.git']]])
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

        stage('Build Evenement-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/woodjooe/Sprng-Devops.git']]])
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

        stage('Build Outil-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/woodjooe/Sprng-Devops.git']]])
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

        stage('Build Publication-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/woodjooe/Sprng-Devops.git']]])
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

        stage('Build Membre-service') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/woodjooe/Sprng-Devops.git']]])
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
        
        stage('Build and Push Docker Image ConfigServer') {
            steps {
                dir('ConfigServer') {
                    // Build Docker image
                    script {
                        sh 'docker build -t oinkoink/sprng-devops:config-server-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         sh 'docker login -u oinkoink -p OinkerOinker'
                         sh 'docker push oinkoink/sprng-devops:config-server-latest'
                          // Run a command inside the Docker container
                       
                        sh 'docker run -d --net host oinkoink/sprng-devops:config-server-latest'
                    }
                }
            }
        
        }
        


        
        stage('Build and Push Docker Image registryService') {
            steps {
                dir('registryService') {
                    // Build Docker image
                    script {
                        sh 'docker build -t oinkoink/sprng-devops:registry-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push oinkoink/sprng-devops:registry-service-latest'
                         sh 'docker run -d oinkoink/sprng-devops:registry-service-latest'
                    }
                }
            }
        
        }

        stage('Build and Push Docker Image Gateway-service') {
            steps {
                dir('Gateway-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t oinkoink/sprng-devops:gateway-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                       
                         sh 'docker push oinkoink/sprng-devops:gateway-service-latest'
                         sh 'docker run -d oinkoink/sprng-devops:gateway-service-latest'
                    }
                }
            }
        
        }
        
        stage('Build and Push Docker Image Evenement-service') {
            steps {
                dir('Evenement-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t oinkoink/sprng-devops:evenement-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push oinkoink/sprng-devops:evenement-service-latest'
                         sh 'docker run -d oinkoink/sprng-devops:evenement-service-latest'
                    }
                }
            }
        
        }
        
        stage('Build and Push Docker Image Outil-service') {
            steps {
                dir('Outil-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t oinkoink/sprng-devops:outil-service-latest .'
                        
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push oinkoink/sprng-devops:outil-service-latest'
                         sh 'docker run -d oinkoink/sprng-devops:outil-service-latest'
                    }
                }
            }
        
        }
        
        stage('Build and Push Docker Image Publication-service') {
            steps {
                dir('Publication-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t oinkoink/sprng-devops:publication-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push oinkoink/sprng-devops:publication-service-latest'
                         sh 'docker run -d oinkoink/sprng-devops:publication-service-latest'
                    }
                }
            }
        
        }
        
        stage('Build and Push Docker Image Membre-service') {
            steps {
                dir('Membre-service') {
                    // Build Docker image
                    script {
                        sh 'docker build -t oinkoink/sprng-devops:membre-service-latest .'
                        
                    }

                    // Push Docker image
                    script {
                         
                         sh 'docker push oinkoink/sprng-devops:membre-service-latest'
                         sh 'docker run -d oinkoink/sprng-devops:membre-service-latest'
                    }
                }
            }
        
        }
    }
}
