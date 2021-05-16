pipeline:
  agent:
    any:
  stages:
    - stage: "Versions Check"
      steps:
        - sh "mvn -version"
        - sh "java -version"
        - sh "git --version"
        - sh "docker --version"

    - stage: "Build Artifacts"
      steps:
        - git "https://github.com/devopsmhk/hello-world.git"
        - sh 'mvn clean install package'

    - stage: "Build Docker Image"
      steps:
        - sh "cp -f webapp/target/webapp.war /opt/docker"
        - sh "cd /opt/docker"
        - sh "sudo docker build -t wms1_demo ."

    - stage: "Run Container"
      steps:
        - sh "sudo docker run -d --name wms1_demo -p 8090:8080 wms1_demo"
