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

### 2. PS







      
