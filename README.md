# AA 공부 노트

## [1회] RPA 자동화 (Robotic Process Automation) 시작하기

- 출처
~~~
https://www.youtube.com/watch?v=OfzPq0eEhMg&list=PLzTsXOWovOskEX3RWLN5KjoGE9fKw61iS
~~~


### RPA 개요
- Digital Workforce 는 사람이 컴퓨터에서 작업하는 업무를 그대로 모방하여 수행하는 Software 로봇
- 자동화 업무 대상 : 정형화된 규칙, 반복적인 업무, 다수의 인원이 필요한 업무, 노동 절약
- 작동원리 : 개발 봇으로 정형화되고 반복적인 업무를 스크립트로 작성, 작성된 스크립트를 사용자 PC에서 실행

### RPA 장점
 1. 직원 업무시간 절감
 2. 업무 생산성 향상
 3. 업무 정확도 향상
 4. 가치 있는 업무에 집중

### AA 공식 매뉴얼
- PDF로 배포하지 않는 이유 : 빠르게 업데이트 되기 때문
~~~
https://docs.automationanywhere.com/ko-KR/
~~~

### 질문하고 싶다면?
- 제일 좋은 방법은 담당자를 찾는 것
~~~
https://apeople.automationanywhere.com/s/?language=en_US
~~~

### AA 기본 명령어
- comment (UiPath의 Log와 같은 기능)
- excel basic (엑셀 안열고 조작)
- excel advanced (엑셀 열고 조작)
- step (UiPath의 Sequence와 같은 기능)
- Tesk Bot (UiPath의 Inboke workflow랑 같은 기능)
- Wait (특정 조건까지 기다리게 하는 명령어)

### 시스템 변수
- 시스템의 정보를 파악하기 위한 변수
<img src="https://user-images.githubusercontent.com/114639257/219285145-79e6509f-4be2-452e-bd24-00d6cc17998e.png" width="400">

### 사용자 변수
- 사용자가 필요에 의해서 만들어서 사용하는 변수
- 상황에 따라서 어떤 변수를 만들지 정의해야 함
~~~
Ex) Number : 123, String : abc
~~~

### A2019 자주 사용하는 명령어
- Universal Recoder (uipath랑 같은 기능)
- Recoder (action 중 하나로 Select, set text(type into),append text(이어 쓰기), click(백그라운드) 등 선택한 객체에 따라 나오는 기능중 하나 선택 가능)(현재 화면에 보이지 않더라도 한 번 로딩이 끝나면 알아서 이미지를 찾을 수 있음)
- Simulate Keystroke (type into, 특수키도 사용 가능)
- Step
- Comments
- application
- browser
- message box
- delay 
- image Recognition (현재 화면에 보여야만 이미지를 찾을 수 있음)
- Clipboard
- File
- Folder
- Log to File
- Mouse (click은 좌표를 기반, 객체가 없거나 이미지가 안 잡히는 등 기술적인 어려움이 있을 경우 사용)
- PDF (이미지ㆍ텍스트 추출, 복호화, 암호화 등, 이미지 형태로 된 pdf의 텍스트는 추출할 수 없음 이럴 경우 OCR 사용)
- Screen (화면캡처)
- Window
- Loop (for문 While문)
- OCR (기본 엔진은 abbyy finereader 12, ocr 라이센스 무상 제공, 한국어 쓸려면 abbyy parameter 다운받아야 함)
~~~
https://github.com/wonbaepark-bot/AutomationAnywhere
~~~
- FTP/SFTP
- Task Bot (stop, pause, run) (input output선택으로 글로벌 변수를 설정할 수 있음)
- CSV/TXT (파일을 열고 데이터를 읽어 처리할 때 사용)
- IF (uipath 랑 똑같은 듯)
- Prompt
- Wait (delay는 지정한 시간이 지나야 다음 단계가 실행되는 것, wait command는 프로세스가 완료되면 시간이 남았더라도 그냥 넘어감)
- Excel 자동화
- Excel Basic
- Excel Advanced
- String (assign, extract text, length, replace, trim, find)
- Number
- Email (send 말고는 roop command 사용 필수 - deletem, forward, reply, save attachments)
~~~
A2019 Email 기본 사용 순서
1. Connet : Email 서버와 연결 설정
2. Email 명령 사용 : 원하는 Action 사용
3. Disconnect : 사용되었던 Email Session 종료
~~~
- SAP (몇가지 command 제외하고 field path 가 필요함)
- Error Handling (uipath Try catch랑 같은 기능)


## 실습
### 엑셀을 활용한 환율 조회 자동화
<img src="https://user-images.githubusercontent.com/114639257/219551080-4c8e7999-3cf6-4a59-a365-7d27a6f4deb2.png" width="600">

~~~
https://www.oanda.com/currency-converter
~~~

#### 사용 Command
- Step
- Browser
- Simulate Keystrokes
- Excel
- Record
- Delay
- Email

실습하면서 궁금한 점
- Excel 고급 중에서 go to cell 의 옵션 중 [특정 셀] 은 A5 또는 B2:B10 처럼 특정 위치를 지정해줘야 하는데, loop를 돌릴 때 만약에 컬럼의 위치가 바뀌거나 하는 등의 변화가 생긴다면 일일이 엑셀을 확인해서 셀의 위치를 지정해주어야 하는 것인지
- Delay 말고 wait을 쓰면 지정 시간 기다리지 않고 환율이 뜰 때까지만 기다렸다가 뜨면 저장하고 넘어갈 수 있게 만들 수 있을 것 같은데 방법을 한번 찾아봐야 할듯
- 엑셀에서 영어 불러올때 한글 키로 활성화 돼있으면 영어가 안쳐지고 한글이 쳐짐 ex) USD → ㅕㄴㅇ

### 결과

<img src="https://user-images.githubusercontent.com/114639257/219575821-3d4fe4bd-b212-441d-899d-0d1e4eacf221.png" width="600">











