## **UART 통신**

### ◆ UART

<img src="https://user-images.githubusercontent.com/66783849/184471962-418d88fe-956b-4bb0-aa7e-881fe555b9ed.png"> UART 회로
<img src="https://user-images.githubusercontent.com/66783849/184471973-c54010dc-49b9-4ba5-88ea-e131f45b7f7f.png"> 연결방법
<img src="https://user-images.githubusercontent.com/66783849/184471985-7778ecee-75fb-46d1-8d24-21deb37793e9.png"> UART 통신

- UART(universal asynchronous receiver/transmitter : 범용 비동기화 송수신기)는 시리얼 통신을 담당하는 회로를 말한다.
- UART는 일반적으로 EIA RS-232, RS-422, RS-485와 같은 통신 표준과 함께 사용한다.
- 병렬 데이터를 직렬화하여 통신하는 개별 집적 회로이다.
- 시리얼 통신 연결은 TX-RX를 엇갈리게 해야한다.
- 통신 데이터는 메모리 또는 레지스터에 들어 있어 이것을 차례대로 읽어 직렬화 하여 통신한다.
- 최대 8비트가 기본 단위이다.
- <img src="https://user-images.githubusercontent.com/66783849/184471908-34c63a6f-b9aa-4057-8869-c8bf1b1a08af.png" width="80%"> 데이터 송 수신 형태
  - 시작 비트 : 통신의 시작을 의미. 한 비트 시간 길이 만큼 유지.
  - 데이터 비트 : 5~8비트의 데이터를 전송. 몇 비트를 사용할 것인지는 해당 레지스터 설정에 따라 결정.
  - 패리티 비트 : 오류 검증을 하기 위한 패리티 값을 생성하여 송신하고 수신쪽에 오류 판단한다.
  - 끝 비트 : 통신 종료를 알린다. 세가지의 정해진 비트 만큼 유지해야 한다. 1, 1.5, 2비트로 해당 레지스터 설정에 따라 결정된다.


<br><br><br>

## 참고문헌
- 시리얼 통신 기초 – UART
  - https://www.hardcopyworld.com/?p=2080
  - https://ko.wikipedia.org/wiki/UART
