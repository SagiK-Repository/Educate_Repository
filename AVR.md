문서정보 : 2022.08.20. 작성, 작성자 [@SAgiKPJH](https://github.com/SAgiKPJH)


# **AVR**

![image](https://user-images.githubusercontent.com/66783849/184473047-ce7d183f-4631-4610-bf3d-78c454bd44d6.png) AVR Atmega8

### ◆ Atmel AVR
- 아트멜 AVR(Atmel AVR)은 1996년 아트멜 사에서 개발된 하버드 구조로 수정한 8비트 RISC 단일칩 마이크로컨트롤러이다.
- 다음과 같은 시리즈가 존재한다.
  - tinyAVR
  - megaAVR
  - XMEGA
  - Application-specific AVR
  - FPSLIC (AVR에 FPGA 추가)
  - 32-bit AVRs

![image](https://user-images.githubusercontent.com/66783849/184473085-06d17383-b95a-4f3a-be0c-6710aa0843bc.png) ISP 연결 커넥터  


### ◆ ISP
- ISP(in-system programming)는 가장 일반적인 방법이다.
- 가장 일반적인 AVR 프로그램 인터페이스 방법으로, 프로그램 전송 방식은 기능적으로 SPI 방법에 Reset 선을 추가한 것이다.  

# **AVR 활용한 Programming**

### ◆ 준비물
- AVR Atmega128A
- AVR USBISP (프로그래밍 인터페이스)
- Microchip Studio (프로그래밍 프로그램)
- ![image](https://user-images.githubusercontent.com/66783849/184473148-b9f37acf-a130-420f-9b44-383f5ea00929.png) ISP 스위치
  - 1번 on : USB 전원사용
  - 2번 on : 3.3V, off : 5V 사용
  - > 1번 on, 2번 on 상태로 설정
-  Wi-Fi 모듈의 입력전원은 3.3V이기 때문에 별도의 전원공급장치를 준비한다.

![image](https://user-images.githubusercontent.com/66783849/184473554-36e93b15-da7a-40ed-89a0-c670327f7415.png) AVR USB ISP
![image](https://user-images.githubusercontent.com/66783849/184473558-cb6a6da6-a792-42f1-a5ac-ed9eaa87d333.png) AVR Atmega128  

![image](https://user-images.githubusercontent.com/66783849/184473565-c70f214f-8be1-4230-a10d-a97499354dfd.png) 
![image](https://user-images.githubusercontent.com/66783849/184473568-18f3eebb-65cf-4fee-9dbf-04219b27acf8.png) Microchip Studio  

<img src="https://user-images.githubusercontent.com/66783849/184473600-5791c7e7-3462-48ea-a427-edc1014bdc55.png" width="60%"> AVR Atmega128 - WiFi 모듈 연결도
<img src="https://user-images.githubusercontent.com/66783849/184473613-d4932136-9542-4fa8-8bd2-ae6450cb2b80.png" width="80%"> 연결모습

![image](https://user-images.githubusercontent.com/66783849/184473624-3688a347-506f-4823-b0fe-c138ee13d69f.png) 사용자 외부전원 보드

<br>

### ◆ MicroChip Studio 프로젝트 설정
1) 새 프로젝트 생성 (폴더에 한글이 없도록 한다)  
  ![image](https://user-images.githubusercontent.com/66783849/184473532-929037d0-882f-4b63-960b-49275ba62df1.png) 새 프로젝트
2) Device 선택 (Atmega128A)  
  ![image](https://user-images.githubusercontent.com/66783849/184473544-c4d8a3c7-dfea-4394-8068-697480427339.png) Device Selection

<br>

### ◆ MicroChip Studio 프로그래밍 준비
 1) AVR과 AVR-ISP를 연결한 후 컴퓨터에 연결한다.
 2) 장치관리자를 통해 AVR ISP의 COM를 알아낸다.
 3) Microchip Studio에 AVR ISP 연결여부를 확인한다.
    - Tools > Add target에서 Select Tool : STK500을 입력하고 COM번호를 등록한다.  
      ![image](https://user-images.githubusercontent.com/66783849/184473757-ac24daf0-538f-4471-82e0-37611914365f.png) Tools > Add Target  
    - View > Available Microchip Tools를 통해 연결장비를 관리한다.  
      ![image](https://user-images.githubusercontent.com/66783849/184473846-7d6a9cc0-6b07-4bcc-aecb-e091ab23c586.png) View > Available Microchip Tools  
    -  Tools > Device Pack Manager를 통해 ATmega_DFP를 Install한다.  
      ![image](https://user-images.githubusercontent.com/66783849/184473767-85436ca0-0257-4d1f-a96e-3f25affb7357.png) Tools > Device Pack Manager  
    -  Tools > Device Programming으로 프로그래밍 수단을 선택한다.
    이후 AVR ISP TOOL 및 COM번호를 입력한다.  
    ![image](https://user-images.githubusercontent.com/66783849/184473781-1507bbf7-6f5b-4c01-acaf-9e7e88c1a0ca.png) Tools > Device Programming을 통해 정상연결을 확인하는 모습  

![image](https://user-images.githubusercontent.com/66783849/184473789-7e41ba05-6d6d-4410-bbd0-1ef305722048.png) Tool Setting 완료 화면

- 이때 Device Programming 창의 Interface의 선택목록이 존재하고, Device signature의 read를 클릭했을 때 AVR의 고유번호가 나타나면 정상작동됨을 알 수 있다.  

  ![image](https://user-images.githubusercontent.com/66783849/184473792-9cbff1d0-eca4-4cf0-8ee6-45b0cc3abdde.png) 생성 오류 창

<br>

### ◆ MicroChip Studio 정상작동 확인 프로그램 Test
- AVR이 정상작동하는지 확인하기 위해 간단한 LED깜빡임 프로그래밍을 진행한다.

#### AVR Atmega128 LED TEST (main.c)
```cpp
#define F_CPU 16000000UL
#include <xc.h>
#include <avr/io.h>
#include <avr/delay.h>

int main(void) {
 DDRD = 0xFF;
 int i = 0;
 
 while(1) {
  i+=10;
  PORTD=0xFF;
  for(int j=0;j<i;j++) _delay_ms(1);
  PORTD=0x00;
  for(int j=0;j<i;j++) _delay_ms(1);
  if(i > 1000)i = 0;
 }
 
}
```
![image](https://user-images.githubusercontent.com/66783849/184474106-d390e014-4ab5-4ce4-95ae-04f697e5fc8d.png) 결과화면  


<br>

