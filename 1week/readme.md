# 1주차 
## Introduction

1. 쿠버네티스
    -  서버 자원을 효율적으로 쓰기 위해 가상화 기술 사용
    - history
        - linux 자원격리 기술 => VM 가상화 기술 (Openstack)
        - dot cloud 가 container 를 만들고 docker 라고 이름 지음.
            -  많은 서비스들을 운영하는 역할 x
        - 많은 Container 오케스트레이터들이 존재, 그 중 쿠버네티스 가장유명
        - 클라우드 위에서 쿠버네티스(서비스 운영) 활용

2. 무엇을 배울까?
    - 클러스터를 운영하는 운영자.
    - 클러스터 기능을 활용하여 서비스를 배포하는 사용자.
    - 사용자 기능에 대해 중심적.
    

## 1Section

1. why kubernetes?
    - 1 system on 1 server
        - 각 system이 필요한 시간대가 다르면, server 가 논다.
        - 백업 서버를 시스템마다 준비해놔야 함.
    - kub
        - Auto scaling을 통하여 트래픽양에 따라 서비스의 자원량 제공
        - auto healing 여분의 서버를 통하여, 각 시스템마다 백업 서버를 준비할 필요 없음
        - deployment (version up) 정책도 중단, 무중단에 따라 다양하게 준비.

2. VM vs Container

    ![VMvsContainer](https://user-images.githubusercontent.com/45062255/107105737-2c5cca00-686b-11eb-9f73-439624e830fb.PNG)

    - container engine : docker
    - container 정의 : linux 버전 별 lib파일, 해당 컨테이너 이미지를 가져오면, 자신의 이미지 안에 있는 오픈스택 라이브러리를 사용하기 때문에(도커의 역할) 해당 컨테이너의 어플리케이션이 작동할 수 있는 환경을 만들어 줌.
    - 도커의 역할2 : name Space(커널) 와 cgroup(자원)을 통해 호스트 리소스를 할당함
    - linux 에서 window 용! 컨테이너 사용 x, 해당 컨테이너가 필요한 자원의 종류가 다른가 봄...
    
    - kub
        - pod 는 하나 이상의 컨테이너를 포함하고, pod 단위로 배포한다.
        - 쿠버네티스는 부하가 많이 걸리는 기능만 확장 가능.


3. application 쿠버네티스 배포 과정


    - hello.js 를 생성하고 해당 파일을 도커에서 container 화, 쿠버네티스에서 pod 화 시키는지 시각적으로 확인.

       ![startKub](https://user-images.githubusercontent.com/45062255/107106424-f4578600-686e-11eb-97b6-1d84d1b59e3e.PNG)
    - container 상태를 알아보기 위한 ps 명령어
    - docker build -t repo/app_name .
        - -t + 레파지토리 + / + 파일이름+ : + version (기재 안할경우 latest) + docker 명세파일 ( Dockerfile 이라는 이름으로 명세할 경우 . 으로 표시)
        - docker exec -it 컨테이너ID /bin/bash 를 통해 컨테이너 내부로 들어갈 수 도 있음.