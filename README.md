# Docker-hoon
# 도커 개요

- 도커를 사용하는 이유?
    
    어떠한 프로그램을 다운 받는 과정을 간단하게 만들기 위해서.
    
    예시를 보면서 말해보자.
    
    - 도커 없이 프로그램을 받을때: installer 다운 ⇒ installer 실행 → 프로그램 설치 완료
    - 하지만... 이럴경우 에러가 발생한다( 갖고 있는 서버, 패키지 버전, 운영체제 등등에 의해..)
    - 따라서 에러도 많이 발생하고 설치 과정이 까다롭다.
    
    그렇지만 도커를 이용해서 받을때의 차이점은
    
    - 67명령어 한번에 딱..!
    
    사실상 도커를 사용하지 않고도 응용 프로그램들을 설치하고 사용 할 수 있다. 하지만 도커를 쓰면 복잡한 과정들을 생략할 수 있어서 편리하다.
    
- 도커란 무엇인가?
    
    도커 정의(위키): 도커는 리눅스의 응용 프로그램들을 프로세스 격리 기술들을 사용해 컨테이너로 실행하고 관리하는 오픈 소스 프로젝트이다.
    
    컨테이너를 사용하여 응용프로그램을 더 쉽게 만들고, 배포하고, 실행할 수 있도록 설계된 도구이며 컨테이너 기반의 오픈소스 가상화 플랫폼이며 생태계 입니다.
    
- 컨테이너란
    
    ### 컨테이너란?
    
    코드와 모든 종속성을 패키지화하여 응용 프로그램이 한 컴퓨팅 환경에서 다른 컴퓨팅 환경으로 빠르고 안정적으로 실행되도록 하는 소프트웨어의 표준 단위이다.
    
    *다양한 프로그램, 실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 프로그램의 배포 및 과리를 단순하게 해줌. 일반 컨테이너의 개념에서 물건을 쉽게 운송 해주는 것 처럼 프로그램을 손쉽게 이동 배포 관리를 할 수 있게 해줍니다. AWS, Azure, GCP등 어디에서든 실행 가능하게 해줍니다.*
    
- 컨테이너 이미지
    
    `컨테이너 이미지`는 코드, 런타임, 시스템 도구, 시스템 라이브러리 및 설정과 같은 응용 프로그램을 실행하는데 필요한 모든 것을 포함하는 가볍고 독립적이며 실행 가능한 소프트웨어 패키지 이다.
    
    도커 이미지는 프로그램을 실행하는데 필요한 설정이나 종속성을 갖고 있으며. 이미지를 이용해서 컨테이너를 생성하고 컨테이너를 이용해서 프로그램을 실행한다
    
- 도커 사용할때의 흐름
    
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dfd27df5-cab4-4ada-996f-f0a034c4590a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dfd27df5-cab4-4ada-996f-f0a034c4590a/Untitled.png)
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b301bccc-87fc-4f48-8a5c-4c145dd867e2/Untitled.png)
    
    1. 먼저 도커 CLI에 커맨드를 입력한다.
    2. 그러면 도커 서버 (도커 Daemon)이 그 커맨드를 받아서 그것에 따라 이미지를 생성하든 컨테이너를 실행하든 모든 작업을 하게된다.
- 도커와 기존의 가상화 기술의 차이를 통한 컨테이너 이해
    
    ## 가상화 기술 나오기 전
    
    - 한대의  서버를 하나의 용도로만 사용
    - 남는 서버 공간 그대로 방치
    - 하나의 서버에 하나의 운영체제, 하나의 프로그램만을 운영
    - 안정적이였으나 비 효율적
    
    때문에 하이퍼 바이저 기반의 가상화가 출현을 했다.
    
    ## 하이퍼 바이저는
    
    - 논리적으로 공간을 분할하여 VM이라는 독립적인 가상 환경의 서버 이용 가능.
    - 하피어 바이저는 호스트 시스템에서 다수의 게스트 OS를 구동할 수 있게 하는 소프트웨어
    - 그리고 하드웨어를 가상화하면서 하드웨어와 가각의 VM을 모니터링 하는 중간 관리자이다.
    
    ## 하이퍼 바이저 기반의 가상화 출현
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f87948a9-457d-41ed-bbad-b092b37ad223/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f87948a9-457d-41ed-bbad-b092b37ad223/Untitled.png)
    
    ## 도커와 하이퍼 바이저 기반 가상화의 공통점과 차이점
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bbb44bcc-acc3-4c2b-8ce5-d3792e422426/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bbb44bcc-acc3-4c2b-8ce5-d3792e422426/Untitled.png)
    
    공통점
    
    - 기본 하드웨어에서 격리된 환경 내에 애플리케이션을 배치하는 방법이다.
    
    차이점
    
    - 가장 큰 차이점은 격리된 환경을 얼마나 격리시키는지에 있다.
    
    또한 각종 시스템 자원을 가상화하고 독립된 공간을 생성하는 작업은 하이퍼바이저를 반드시 거치기 때문에 일본 호스트에 비해 성능의 손실이 발생한다. 그 뿐만 아니라 가상 머신은 게스트 운영체제를 사용하기 위한 라이브러리, 커널 등을 전부 포함하기 때문에 가상 머신을 배포하기 위한 이미지로 만들었을 때 이미지의 크기 또한 커집니다.즉 가상머신은 완벽한 운영체제를 생성할 수 있다는 장점은 있지만 일반 호스트에 비해 성능 손실이 있으며, 수 기가바이트에 달하는 가상 머신 이미지를 애플리케이션으로 배포하기는 부담스럽다는 단점이 있다.
    
    ### 결론
    
    - 도커는 VM과 비교했을때 컨테이너는 하아퍼 바이저와 게스트 OS가 필요하지 않으므로 더 가볍다(오버헤드가 적다) (VM은 무거운 `게스트 OS`까지 있음)
    - 어플리케이션을 실행할때는 컨테이너 방식에서는 호스트 OS 위에 어플리케이션의 실행 패키지인 이미지를 배포하기만 하면 되는데 VM은 어플리케이션을 실행 하기 위해서 VM을 띄우고 자원을 할당해야 한다.
    - 게스트 OS를 부팅하여 어플리케이션을 실행 해야 해서 훨씬 복잡하고 무겁게 실행을 해야합니다.
    
    ### 도커 컨테이너
    
    `도커 컨테이너`에서 돌아가는 애플리케이션은 컨테이너가 제공하는 격리 기능 내부에 샌드박스가 있지만, 여전히 같은 호스트의 다른 컨테이너와 동일한 커널을 공유한다. 결과적으로, 컨테이너 내부에서 실행되는 프로세스는 호스트 시스템(모든 프로세스를 나열할 수 있는 충분한 권한 있음)에서 볼 수 있다. 예를 들어, 도커와 함께 몽고 DB 컨테이너를 시작하면 호스트의 일반 쉘에 ps-e grep 몽고를 실행하면 프로세스가 표시됩니다.
    또한 컨테이너가 전체 OS를 내장할 필요가 없는 결과, 그것들은 매우 가볍고, 일반적으로 약 5-100MB이다.
    
    ## 어떻게 도커 컨테이너를 격리시킬까?
    
    먼저 `리눅스`에서 쓰이는 `Cgroup`(control groups)과 `네임스페이스`(namespace)에 대해서 알야아 한다.
    
    이것들은 컨테이너와 호스트에서 실행되는 다른 프로세스 사이에 벽을 만드는 리눅스 커널 기능들이다.
    
    ### Chroot
    
    root 디렉터리를 변경하여 특정 프로세스가 상위 디렉터리에 접근할 수 없도록 격리시킬 수 있다. 정확히 이 역할을 하는것이 Chroot이다.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4b6129cf-45e5-4024-bfbe-6097095a376f/Untitled.png)
    
    ### Cgroup
    
    CPU, 메모리, Network Bandwith, HD i/o 등 프로세스 그룹의 시스템 리소스 사용량을 관리하는 기능 ⇒ 어떤 어플이 사용량이 너무 많다면 그 어플리 케이션 같은 것을 C group에 집어 넣어서 `CPU와 메모리 사용 제한 기능`
    
    ### namespace
    
    하나의 시스템에서 프로세스를 격리시킬 수 있는 `가상화 기술` 별개의 독립된 공간을 사용하는 것 처럼 격리된 환경을 제공하는 경량 프로세스 가상화 기술
    
- 이미지로 컨테이너 만들기
    
    ## 시작하기 전에 기억해야 할 것
    
    *이미지는 응용 프로그램을 실행하는데 **필요한 모든 것**을 포함하고 있습니다.*
    
    `필요한 모든 것` : 
    1. 컨테이너가 시작될 때 실행되는 **명령어** ex) run kakaotalk 
    
    1. **파일 스냅샷** ex)컨테이너에서 카카오톡을 실행하고 싶다면 카카오톡 파일(카카오톡을 실행하는데 필요한 파일)스냅샷
    - 파일 스냅샷은 디렉토리나 파일을 카피 한것.
    
    ## 이미지로 컨테이너를 만드는 순서
    
    1. Docker 클라이언트에 `docker run <이미지>` 입력
    2. 도커 이미지에 있는 파일 스냅샷을 컨테이너 하드 디스크에 옮겨 줍니다.
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/89e2f4d1-466d-460e-b1de-64e3648445e6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/89e2f4d1-466d-460e-b1de-64e3648445e6/Untitled.png)
    
    1. 이미지에서 가지고 있는 명령어(컨테이너가 실행될때 사용될 명령어들)를 이용해서 카카오톡을 실행시켜줌
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/474f36c4-d501-476d-a2ea-387adc8604b6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/474f36c4-d501-476d-a2ea-387adc8604b6/Untitled.png)
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69c673eb-40a3-4db3-8aec-9e6545fe12cb/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69c673eb-40a3-4db3-8aec-9e6545fe12cb/Untitled.png)
    
- Namespace와 Cgroup은 리눅스 기능인데 어떻게 내컴퓨터(맥)에서 사용할 수 있는것인가?
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45b16bef-a10b-4afe-b685-3933ff4c8209/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45b16bef-a10b-4afe-b685-3933ff4c8209/Untitled.png)
    
    내부적으로는 그림과 같이 작동한다.
    

# 기본적인 도커 명령어

- 이미지 내부 파일 시스템 구조 보기
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9f03deb-60b4-476e-9355-59be7cc540cf/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9f03deb-60b4-476e-9355-59be7cc540cf/Untitled.png)
    
    ex) docker run alpine ls → 
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4aaf02db-bf0d-4edc-bad1-201e82a18f4e/Untitled.png)
    
- 컨테이너들 나열하기
    
    $ docker ps
    
- 도커 컨테이너 생명주기
    
    ## 1.생성, 실행
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d8d4b3f9-b8ac-4984-84da-93e8d86e82cd/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d8d4b3f9-b8ac-4984-84da-93e8d86e82cd/Untitled.png)
    
    `docker run start`  = `docker create <이미지 이름>` + `docker start <시작할 컨테이너 아이디/이름>`
    
    ## 2.실행 → 중지
    
    - 실행 → 중지에선 두가지 방법이 존재함.
        - docker stop <중지할 컨테이너 아이디/이름>
        - docker kill <중지할 컨테이너 아이디/이름>
    
    ### Stop과 Kill은 어떤 차이가 있을까?
    
    공통점은 둘다 실행중인 컨테이너를 중지시킨다 하지만
    
    `STOP`은 Gracefully하게 중지를 시킵니다.
    
    - 자비롭게 그동안 하던 작업들을(메시지를 보내고 있었다면 보내고 있던 메시지) 완료하고 컨테이너를 중지시킴
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d7341fe-ba7a-479a-92b4-bbfbdc1ea95e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d7341fe-ba7a-479a-92b4-bbfbdc1ea95e/Untitled.png)
    
    `KILL`같은 경우는 `stop`과 달리 어떠한 것도 기다리지 않고 바로 컨테이너를 중지시킨다.
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0e365afa-7a07-4830-a3a4-3ca9d7ac5549/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0e365afa-7a07-4830-a3a4-3ca9d7ac5549/Untitled.png)
    
    ## 3. 삭제
    
    ### 중지된 컨테이너 삭제하기
    
    `docker rm <아이디/이름>`
    
    - 실행중인 컨테이너는 먼저 중지한 후에 삭제 가능
    
    ### 모든 컨테이너를 삭제하고 싶다면
    
    `docker rm `docker ps -a -q``
    
    ### 이미지를 삭제하고 싶다면
    
    `docker rmi <이미지 id>`
    
    ### 한번에 컨테이너, 이미지, 네트워크 모두 삭제하고 싶다면
    
    `docker system prune`
    
    - 도커를 쓰지 않을때 모두 정리를 하고싶을때 사용해주면 좋음
    - 하지만 실행중인 컨테이너에는 영향을 주지 않는다.
- 실행중인 컨테이너에 명령어 전달
    
    ### docker exec <컨테이너 아이디>
    
    ## docker run vs docker exec
    
    - docker run은 `새로운 컨테이너`를 만들어서 실행
    - docker exec는 이미 `실행중인 컨테이너`에 명령어를 전달
- 레디스를 이용한 컨테이너 이해
    
    **목표:** 격리된 컨테이너 안에 있는 컴포넌트에 접근해보기
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2baebf1f-9d9b-4bb5-99b4-91f37cf73be1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2baebf1f-9d9b-4bb5-99b4-91f37cf73be1/Untitled.png)
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce7a2562-d7d2-41cc-942f-45d681f8b196/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce7a2562-d7d2-41cc-942f-45d681f8b196/Untitled.png)
    
    해결 방법
    
    - 레디스 클라이언트도 컨테이너 안에서 실행을 시켜야한다
    - `docker exec -it <컨테이너id> redis-cli`
    - `-it` 옵션은 명령어를 실행한 후 계속 명령어를 적을 수 있게 하는 옵션이다
    `-i` interactive 상호적인 
    `-t` terminal
    - -it가 없다면 redis-clis를 키기만 하고 밖으로 다시 나와버린다.
    
- 실행중인 컨테이너에서 터미널 생활 즐기기
    - 앞에서 특정 컨테이너에 대한 명령을 실행할때 docer exec ... 이런 명령어들을 함께 계속 써주었는데 너무 귀찮아 질 때가 있다.
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7a5912a7-e5f9-4922-afd3-eb4b3bd9776b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7a5912a7-e5f9-4922-afd3-eb4b3bd9776b/Untitled.png)
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/136dcf8f-5e74-4b66-8b31-ecd96d3abcb8/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/136dcf8f-5e74-4b66-8b31-ecd96d3abcb8/Untitled.png)
    
    컨테이너 안 shell 환경에 접근 가능하다.
    

## 도커 이미지 만들어 보기

- 도커 이미지 생성하는 순서
    
    dockerfile 작성 → 도커 클라이언트 → 도커 서버 → 이미지 생성
    
    - `도커파일작성`: 도커 이미지를 만들기 위한 설정 파일입니다. 컨테이너가 어떻게 행동해야 하는지에 대한 설정들을 정의해줌.
    - `도커 클라이언트`: 도커 파일에 입력된 것들이 도커 클라이언트에 전달되어야 됩니다.
    - `도커서버`: 도커 클라이언트에 전달된 모든 중요한 작업들을 하는 곳
- dockerfile 만들기
    
    ## 도커 파일이란
    
    - 도커 이미지를 만들기 위한 설정 파일이며, 컨테이너가 어떻게 행동해야 하는지에 대한 설정들을 정의해 주는 곳 입니다.
    
    ### 도커 파일 만들어보기
    
    ```jsx
    #베이스 이미지를 명시해 준다 ex) ubuntu centos aplpine
    FROM baseImage
    
    # 추가직으로 필요한 파일들을 다운로드 받는다
    RUN command
    
    # 컨테이너 시작시 실행될 명령어들을 명시해 준다
    CMD ["executable"]
    ```
    
    ### FROM
    
    이미지 생성시 기반이 되는 이미지 레이어 입니다.
    
    <이미지 이름>:<태그> 형식으로 작성
    
    태그를 안붙이면 자동적으로 가장 최신것으로 다운 받음
    
    ex) ububtu:14.04 
    
    ### RUN
    
    도커 이미지가 생성되기 전에 수행할 쉘 명령어
    
    ### CMD
    
    컨테이너가 시작되었을때 실행할 실행 파일 또는 셸 스크립트 입니다.
    
    해당 명령어는 DockerFile내 1회만 쓸 수 있습니다
    
    ### 베이스 이미지는 무엇인가?
    
    - 도커 이미지는 여러개의 레이어로 되어 있다. 그 중에서 베이스 이미지는 이 이미지의 기반이 되는 부분이다.
    - 레이어는 중간 단계의 이미지라고 생각하면 된다.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eccf4f38-39ed-4ab8-9246-42f683a51eaa/Untitled.png)
    
- dockerfile로 도커 이미지 만들기
    
    ### 완성된 도커 파일로 어떻게 이미지를 생성하나요?
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aaefb6f8-041d-4928-aa01-1350d91c73f7/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aaefb6f8-041d-4928-aa01-1350d91c73f7/Untitled.png)
    
    - 도커 파일에 입력된 것들이 도커 클라이언트에 전달되어서 도커 서버가 인식하게 하여야 합니다. 그렇게 하기 위해서 `docker build ./` 또는 `docker build .`
    
    베이스 이미지에서 다른 종속성이나 새로운 커맨드를 추가 할때는 임시 컨테이너를 만든 후 그 컨테이너를 토대로 새로운 이미지를 만든다. 그리고 그 임시 컨테이너는 지워준다.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4a78a129-9ac7-4bf8-9004-af6f399bff2d/Untitled.png)
    
- 내가만든 이미지 기억하기 쉬운 이름 주기
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68df895f-8d96-49bb-9bfb-753cef4752e6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68df895f-8d96-49bb-9bfb-753cef4752e6/Untitled.png)
    
    docker build -t dudgns3tp/hello:latest ./  이런식으로
    
