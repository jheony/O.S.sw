# O.S.sw
2024_1 오픈소스sw / 과제2.README 파일 작성하기_20213102 윤지현
## 리눅스 명령어 [top, ps, jobs, kill] 조사

### 1. top

- 현재 OS의 상태를 나타내는 도구
   
   - 메모리 사용량, CPU 사용량 등을 나타내며 주기적인 업데이트를 통해 거의 실시간 내용을 보여줌.

- 요약 영역
  
    ![image](https://github.com/jheony/O.S.sw/assets/139779783/08fc9999-76e9-477f-940c-447ed00e22f1)

  - 전체 프로세스가 OS에 대해 리소스를 얼마나 차지하고 있는지 알려줌.
  - 현재 시간, 유저, 로드 애버리지, Tasks, CPU, 메모리 등이 나타남.


  - 로드 애버리지
    - CPU Load(CPU가 수행하는 작업의 양)의 이동 평균
    - 순서대로 1분, 5분, 15분에 대한 평균값임.


  - Tasks
    - 현재 프로세스들의 상태
    - Total : 전체 프로세스, running : 실행중, sleeping : 대기상태, process & stopped : 종료, zombies : 좀비 수

  - CPU 사용량
    - CPU의 사용율을 퍼센테이지로 나누어서 보여줌.
      - us : 유저 영역에서의 CPU 사용률
      - sy : 시스템 프로세스의 CPU 사용률
      - ni : 우선순위로 실행되는 프로세스의 CPU 사용률
      - id : 미사용 비율
      - wa : IO가 완료될 때까지 기다리고 있는 CPU 비율
      - hi : HW 인터럽트에 사용되는 CPU 사용률
      - si : SW 인터럽트에 사용되는 CPU 사용률
      - st : CPU를 VM에서 사용하여 대기하는 CPU 비율

  - 메모리 사용량
    - Mem : RAM의 메모리 영역
    - Swap : 디스크를 메모리처럼 이용, Mem 사용량이 거의 가득 찼을 때 사용
      - total : 총 메모리 양
      - free : 사용 가능한 메모리 양
      - used : 사용중인 메모리 양
    - buff/cache : IO와 관련되어 사용되는 버퍼에 사용되는 메모리

- 디테일 영역

    ![image](https://github.com/jheony/O.S.sw/assets/139779783/b5687134-df44-4f7d-b60f-1d0541d6b0e4)
  - PID : 프로세스 id, 각 프로세스의 고유한 식별번호
  - USER : 해당 프로세스를 실행한 사용자
  - PR & NI
    - PR : 커널에 의해 스케줄링 되는 우선순위, 값이 낮을수록 더 높은 우선순위를 가짐.
    - NI : 사용자에 의해 변경된 프로세스의 우선순위
  - VIRT, RES, SHR, %MEM
    - VIRT : 프로세스가 사용하는 가상 메모리의 크기 (KB)
    - RES : 프로세스가 실제로 점유하고 있는 물리적 메모리의 크기(KB)
    - SHR(Shared Memory) : 다른 프로세스와의 공유하고있는 메모리의 크기(KB)
    - %MEM : RAM에서 RES가 차지하는 비율
  - S : 현재 상태
  - TIME+ : 프로세스가 사용한 누적 CPU 시간
  - COMMAND : 해당 프로세스를 실행한 명령어 OR 프로그램

### 2. ps
   - 현재 실행 중인 프로세스의 정보 제공
     - 프로세스의 상태, 사용 자원, 프로세스 ID 등 확인 가능
     - 시스템 리소스를 소비하는 프로세스 식별, 관련 프로세스 종료 및 조정 가능
   - 옵션, $ps [option]
     - -ef : 모든 프로세스를 풀 포맷으로 출력
     - aux : 실행 중인 모든 프로세스 확인
     - auxf : 실행 중인 프로세스를 트리 구조로 출력
     - -A, -e : 모든 프로세스 출력
     - -a : 세션 리더 제외, 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스 출력
     - -f : full 포맷 출력
     - -u 사용자명 : 지정된 사용자의 프로세스 표시
     - -p 프로세스ID : 지정된 프로세스 ID의 프로세스 표시 
     - -l : 긴 형식으로 출력
     - -x : 로그인 상태에 있는 동안 아직 완료되지 않은 프로세스 출력
   
   - 상태
     
      ![image](https://github.com/jheony/O.S.sw/assets/139779783/a34cce7d-63b8-4d3c-baea-2c4f391b2d13)
      - R : 실행 중
      - S : 대기 상태, 특정 이벤트나 조건 발생할 때 까지 활성화되지 않음
      - T : 중지 or 트레이스/디버그
      - Z : 종료됐지만 부모 프로세스에 의해 아직 회수되지 않음
      - D : 디스크 입출력과 같은 시스템 활동에 의한 대기 상태, 인터럽트 불가능

### 3. jobs
   - 쉘에서 실행한 프로세스 목록 및 백그라운드로 실행중인 프로세스 확인
      ![image](https://github.com/jheony/O.S.sw/assets/139779783/2bcb0434-0725-4d02-8e2c-dd39c7979664)

   - 옵션, $jobs [option] [job]
      - -l : 프로세스 ID와 함께 목록 출력
      - -n : 마지막 알림 이후 변경된 작업 목록만 출력
      - -p : job의 프로세스 ID만 출력
      - -r : 실행중인 job만 출력
      - -s : 중지된 job만 출력
        
   ![image](https://github.com/jheony/O.S.sw/assets/139779783/c0aef631-f36e-46ea-92e6-3d5e849f3f3a)
   - [1]+
     - 대괄호 안 숫자 : job ID
     - -는 +로 표시된 프로세스 종료 시 기본값으로 사용될 프로세스를 의미
       
   - 상태
     - Running         : 실행 중인 작업
     - Done            : 작업 완료 0반환 
     - Done(code)      : 작업 종료, 0아닌 코드 반환
     - Stopped         : 작업 중지
     - Stopped(SIGSTP)   : SIGSTP 시그널 작업 일시 중지
     - Stopped(SIGSTOP)   : SIGSTOP 시그널 작업 일시 중지
     - Stopped(SIGTTIN)   : SIGSTTIN 시그널 작업 일시 중지
     - Stopped(SIGTTOU)   : SIGSTTOU 시그널 작업 일시 중지


### 4. kill
   - 프로세스에 신호를 보내 해당 프로세스를 종료하거나 재시작.
   - 시스템 리소스를 과도하게 사용하거나 응답하지 않는 프로세스 안전하게 종료하는데 유용함
   - 옵션, $kill [option] [process ID]
     - -l : 모든 시그널 목록 표시
     - -s : 지정한 시그널을 보냄
     - -9 : SIGKILL 시그널을 보내 강제 종료
     - -15 : SIGTERMM 시그널을 보내 정상 종료 요청 
   
   - 시그널
     - SIGHUP : 세션 종료
     - SIGINT : 인터럽트
     - SIGKILL : 강제종료
     - SIGTERM : 정상 종료 요청
     - SIGSTOP : 프로세스 일시 정지

      
