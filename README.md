<!-- Source: https://www.jenkins.io/doc/tutorials/build-a-python-app-with-pyinstaller/ -->

```
$ docker network create jenkins
21e3bf66fb09f12d57251d548db2eeb83360a592194344e0b01babcde8026bf9
```

### Docker in Docker!
```
$ docker run \
  --name jenkins-docker \
  --rm \
  --detach \
  --privileged \
  --network jenkins \
  --network-alias docker \
  --env DOCKER_TLS_CERTDIR=/certs \
  --volume jenkins-docker-certs:/certs/client \
  --volume jenkins-data:/var/jenkins_home \
  --publish 2376:2376 \
  --publish 3000:3000 \
  docker:dind \
  --storage-driver overlay2
Unable to find image 'docker:dind' locally
dind: Pulling from library/docker
2408cc74d12b: Pull complete
d991df732aca: Pull complete
21d05af1c410: Pull complete
4a01eeb4b966: Pull complete
0f1647754422: Pull complete
e917105572c1: Pull complete
b709778230e4: Pull complete
94076fc9c77a: Pull complete
1c0650593e05: Pull complete
c8739efbf338: Pull complete
1528486149a1: Pull complete
5fce28207d4c: Pull complete
e2c6543c9821: Pull complete
Digest: sha256:a7a9383d0631b5f6b59f0a8138912d20b63c9320127e3fb065cb9ca0257a58b2
Status: Downloaded newer image for docker:dind
9a14cfd95ea071aeb83b6e5224f8eeb23cde733870630aced42710b72d34818f> saim @ Saims-MBP ~/github/jenkins 19:44:05
```

### Run your own myjenkins-blueocean:2.332.3-1 image as a container in Docker using the following docker run command:
```
$ docker build -t myjenkins-blueocean:2.332.3-1 .
[+] Building 80.0s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                              0.1s
 => => transferring dockerfile: 627B                                                              0.0s
 => [internal] load .dockerignore0.0s
 => => transferring context: 2B  0.0s
 => [internal] load metadata for docker.io/jenkins/jenkins:2.332.3-jdk11                          1.6s
 => [auth] jenkins/jenkins:pull token for registry-1.docker.io                                    0.0s
 => [1/6] FROM docker.io/jenkins/jenkins:2.332.3-jdk11@sha256:9893bfe43a850a0c80a4dc6e40d212e345ce8ad5537a4cf1d3f2033787a43695                                    26.8s
 => => resolve docker.io/jenkins/jenkins:2.332.3-jdk11@sha256:9893bfe43a850a0c80a4dc6e40d212e345ce8ad5537a4cf1d3f2033787a43695                                     0.0s
 => => sha256:aefbd09faf8a21ad0c7fef069be1cf8ac0c895169f6413c00782ecddf5e63991 3.88kB / 3.88kB    0.0s
 => => sha256:9893bfe43a850a0c80a4dc6e40d212e345ce8ad5537a4cf1d3f2033787a43695 1.05kB / 1.05kB    0.0s
 => => sha256:cb535f2a7054fa2bed0ff7b27587f9b5af8bb86e6882c6f71a65d6eebaa07532 15.56kB / 15.56kB  0.0s
 => => sha256:67e8aa6c8bbc76b1f2bccb3864b0887671833b8667dc1f6c965fcb0eac7e6402 54.95MB / 54.95MB 11.3s
 => => sha256:d4b310eb3fdfcb683bbe2198470a6252c9da11e8662035bc41e0b7ba1f6a4c33 52.76MB / 52.76MB  2.7s
 => => sha256:79f2f383117e313edc6815af619c8775b1d9ef8c885cf9e641dd585e59ade400 45.96kB / 45.96kB  0.5s
 => => sha256:8b0534c7187a8d6f3c12ff9388383d4a167a75fb9fbae46bbe9326ff25a18a14 4.25MB / 4.25MB    1.5s
 => => sha256:e4ebc026722c3747759e1749cdc7f4c0f72da0444647864feb8a3b712c64675a 1.80kB / 1.80kB    1.7s
 => => sha256:b8b2b1a015c74435dea8a0249cfc8f5e33f1cb3380296b92e52be1edc7c3c013 188B / 188B        2.0s
 => => sha256:1308663db51fb114174f9e125348fdd69771e8eccf7943e6b44766e85e6ba0d8 5.59kB / 5.59kB    2.4s
 => => sha256:a9980750ebb2299e13d734a7ad3c922775ec77045efb2c4db2c163e360eed00d 375.41kB / 375.41kB2.7s
 => => sha256:771a2a8f36655f529292c8487ea0c72e4de235f2dd1a7a091618db9772e37ee2 94.70MB / 94.70MB  7.7s
 => => sha256:8767b747a3d4be1934b5470d59421428d056620ed93ab7823f0bcbd05dbc6565 5.72kB / 5.72kB    2.9s
 => => sha256:68fbb5fc468dbd31d7efaf7025451e77af1c40406b8e82809ab0d94fe213f578 5.69MB / 5.69MB    4.5s
 => => sha256:76dd80acf4f63e3d7d729d46005e5771a47fa6d739b727f3c199926ea76d42e1 76.51MB / 76.51MB 14.5s
 => => sha256:bb3b9e0921fc149c07259134024299ce8601fad30950f2f2258dd31d700c7859 1.93kB / 1.93kB    8.4s
 => => sha256:f469501b9a4682cda09ee17a4d6f21322314983d3ba0a5362982a4e9a65e3e48 1.31kB / 1.31kB    8.6s
 => => sha256:c35c92bf7d6e381ff5d250b09269ff36b4406e5b6a05f2cb23906ffec75a5083 386B / 386B        8.8s
 => => sha256:e4260d58d0c62dc3a5c806e2645ecafc4afdb91ac53c395d88963c9cc46b8285 375B / 375B        8.9s
 => => sha256:62d1b6acbca23b6d8f57871d96bc09d901f07db452291323e5d53d54acbc615b 3.72kB / 3.72kB    9.0s
 => => extracting sha256:67e8aa6c8bbc76b1f2bccb3864b0887671833b8667dc1f6c965fcb0eac7e6402         4.2s
 => => extracting sha256:d4b310eb3fdfcb683bbe2198470a6252c9da11e8662035bc41e0b7ba1f6a4c33         3.1s
 => => extracting sha256:79f2f383117e313edc6815af619c8775b1d9ef8c885cf9e641dd585e59ade400         0.0s
 => => extracting sha256:8b0534c7187a8d6f3c12ff9388383d4a167a75fb9fbae46bbe9326ff25a18a14         0.3s
 => => extracting sha256:e4ebc026722c3747759e1749cdc7f4c0f72da0444647864feb8a3b712c64675a         0.1s
 => => extracting sha256:b8b2b1a015c74435dea8a0249cfc8f5e33f1cb3380296b92e52be1edc7c3c013         0.0s
 => => extracting sha256:1308663db51fb114174f9e125348fdd69771e8eccf7943e6b44766e85e6ba0d8         0.0s
 => => extracting sha256:a9980750ebb2299e13d734a7ad3c922775ec77045efb2c4db2c163e360eed00d         0.1s
 => => extracting sha256:771a2a8f36655f529292c8487ea0c72e4de235f2dd1a7a091618db9772e37ee2         2.0s
 => => extracting sha256:8767b747a3d4be1934b5470d59421428d056620ed93ab7823f0bcbd05dbc6565         0.0s
 => => extracting sha256:68fbb5fc468dbd31d7efaf7025451e77af1c40406b8e82809ab0d94fe213f578         0.3s
 => => extracting sha256:76dd80acf4f63e3d7d729d46005e5771a47fa6d739b727f3c199926ea76d42e1         3.0s
 => => extracting sha256:bb3b9e0921fc149c07259134024299ce8601fad30950f2f2258dd31d700c7859         0.0s
 => => extracting sha256:f469501b9a4682cda09ee17a4d6f21322314983d3ba0a5362982a4e9a65e3e48         0.0s
 => => extracting sha256:c35c92bf7d6e381ff5d250b09269ff36b4406e5b6a05f2cb23906ffec75a5083         0.0s
 => => extracting sha256:e4260d58d0c62dc3a5c806e2645ecafc4afdb91ac53c395d88963c9cc46b8285         0.0s
 => => extracting sha256:62d1b6acbca23b6d8f57871d96bc09d901f07db452291323e5d53d54acbc615b         0.0s
 => [2/6] RUN apt-get update && apt-get install -y lsb-release                                    8.3s
 => [3/6] RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc     https://download.docker.com/linux/debian/gpg                                          0.5s
 => [4/6] RUN echo "deb [arch=$(dpkg --print-architecture)     signed-by=/usr/share/keyrings/docker-archive-keyring.asc]     https://download.docker.com/linux/de  0.4s
 => [5/6] RUN apt-get update && apt-get install -y docker-ce-cli                                 14.0s
 => [6/6] RUN jenkins-plugin-cli --plugins "blueocean:1.25.5 docker-workflow:1.28"               26.8s
 => exporting to image           1.2s
 => => exporting layers          1.2s
 => => writing image sha256:4bbf331f7d9b4af7766bb34bcbd76428f15e86828f10edfd760cce3df40ed79e      0.0s
 => => naming to docker.io/library/myjenkins-blueocean:2.332.3-1                                  0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

```
> saim @ Saims-MBP ~/github/jenkins 19:48:36
$ docker run \
>   --name jenkins-blueocean \
>   --detach \
>   --network jenkins \
>   --env DOCKER_HOST=tcp://docker:2376 \
>   --env DOCKER_CERT_PATH=/certs/client \
>   --env DOCKER_TLS_VERIFY=1 \
>   --publish 8080:8080 \
>   --publish 50000:50000 \
>   --volume jenkins-data:/var/jenkins_home \
>   --volume jenkins-docker-certs:/certs/client:ro \
>   --volume "$HOME":/home \
>   --restart=on-failure \
>   --env JAVA_OPTS="-Dhudson.plugins.git.GitSCM.ALLOW_LOCAL_CHECKOUT=true" \
>   myjenkins-blueocean:2.332.3-1
cb807060b4aff0f73cb9666b5f7c2be4c32f122fbed58bc48544e510b5eb82bc
```

```
$ docker container ls --format='{{json .}}' | jq .
{
  "Command": "\"dockerd-entrypoint.…\"",
  "CreatedAt": "2022-06-20 20:26:35 -0400 EDT",
  "ID": "9b273da0b328",
  "Image": "docker:dind",
  "Labels": "",
  "LocalVolumes": "3",
  "Mounts": "0352af647032f8…,jenkins-docker…,jenkins-data",
  "Names": "jenkins-docker",
  "Networks": "jenkins",
  "Ports": "0.0.0.0:2376->2376/tcp, :::2376->2376/tcp, 2375/tcp, 0.0.0.0:3000->3000/tcp, :::3000->3000/tcp",
  "RunningFor": "9 minutes ago",
  "Size": "14.7kB (virtual 312MB)",
  "State": "running",
  "Status": "Up 8 minutes"
}
{
  "Command": "\"/sbin/tini -- /usr/…\"",
  "CreatedAt": "2022-06-20 19:56:55 -0400 EDT",
  "ID": "cb807060b4af",
  "Image": "myjenkins-blueocean:2.332.3-1",
  "Labels": "org.opencontainers.image.source=https://github.com/jenkinsci/docker,org.opencontainers.image.version=2.332.3,desktop.docker.io/binds/2/Target=/home,org.opencontainers.image.licenses=MIT,org.opencontainers.image.description=The Jenkins Continuous Integration and Delivery server,org.opencontainers.image.revision=625c241aa13b804f0f3947fad43c997dae7452fb,org.opencontainers.image.title=Official Jenkins Docker image,org.opencontainers.image.url=https://www.jenkins.io/,org.opencontainers.image.vendor=Jenkins project,desktop.docker.io/binds/2/Source=/Users/saim,desktop.docker.io/binds/2/SourceKind=hostFile",
  "LocalVolumes": "2",
  "Mounts": "jenkins-docker…,/host_mnt/User…,jenkins-data",
  "Names": "jenkins-blueocean",
  "Networks": "jenkins",
  "Ports": "0.0.0.0:8080->8080/tcp, :::8080->8080/tcp, 0.0.0.0:50000->50000/tcp, :::50000->50000/tcp",
  "RunningFor": "38 minutes ago",
  "Size": "3.35MB (virtual 786MB)",
  "State": "running",
  "Status": "Up 6 minutes"
}
```

## Mapping of volume
#### `/home` in the container is mapped to `/Users/saim` on the local Mac machine

```
> saim @ Saims-MBP ~/github/jenkins 20:47:34
$ docker exec jenkins-blueocean ls /Users/saim/github/jenkins/simple-python-pyinstaller-app
ls: cannot access '/Users/saim/github/jenkins/simple-python-pyinstaller-app': No such file or directory

> saim @ Saims-MBP ~/github/jenkins 20:47:41
$ docker exec jenkins-blueocean ls /Users/saim/github/jenkins
ls: cannot access '/Users/saim/github/jenkins': No such file or directory

> saim @ Saims-MBP ~/github/jenkins 20:47:47
$ docker exec jenkins-blueocean ls /home/github/jenkins/simple-python-pyinstaller-app
README.md
jenkins
sources
```

## Pipeline-as-code
This is the foundation of "Pipeline-as-Code", which treats the continuous delivery pipeline a part of the application to be versioned and reviewed like any other code. Read more about Pipeline and what a Jenkinsfile is in the Pipeline and Using a Jenkinsfile sections of the User Handbook.