# TCP 3 way handshake & 4 way handshake

### 

### reference

- [[네트워크] 3-way / 4-way Handshake 란? (tistory.com)](https://bangu4.tistory.com/74)



## 3 way handshake

> 정확한 전송을 보장하기 위해 연결을 성립하기까지 거치는 과정

- SYN: 보내는 것
- ACK: 받았다는 신호

### 

### 과정

- 클라이언트 SYN (x) → 서버
  - 상태
    - 클라이언트: SYN_SENT
    - 서버: Wait for Client
  - 🧠: 클라이언트 쪽에서 하나를 보내 본다
- 서버 ACK(x + 1), SYN(y) → 클라이언트
  - 상태
    - 서버: SYN_RECEIVED
  - 🧠: 서버가 클라이언트 것을 잘 받는 것 확인 후 서버 쪽에서도 하나를 보내 본다
- 클라이언트 ACK(y + 1) → 서버
  - 상태
    - 서버: ESTABLISHED
  - 🧠: 클라이언트도 서버 것을 잘 받는 것 확인 되면 전송이 잘 된다고 판단 → 연결 성립



## 4 way handshake

> 연결을 해제하기 전 모든 통신이 끝난 것을 확인하는 과정

- FIN: 연결 종료 플래그
  - 🧠: 나는 볼일 끝~~ 이라고 말해주는 것

### 

### 과정

- 클라이언트 FIN → 서버
  - 상태
    - 클라이언트: FIN_WAIT
- 서버 ACK → 클라이언트
  - 상태
    - 서버: CLOSE_WAIT
    - 🧠: 아직 덜 보낸 데이터 있을 수 있으니 바로 닫지 않고 대기
- 서버 데이터 전송 완료 후 FIN → 클라이언트
  - 상태
    - 서버: LAST_ACK
- 클라이언트 ACK → 서버
  - 상태
    - 클라이언트: TIME_WAIT
    - 🧠: 서버는 데이터를 다 보냈지만 전송에 소요되는 시간이 있어 클라이언트는 아직 덜 받았을 수 있으니 대기
- 서버는 ACK 확인 후 소켓 Closed, 클라이언트는 TIME_WAIT 끝나면 소켓 Closed
  - 🧠: 클라이언트 볼 일 끝 → 서버 데이터 떨이 → 클라이언트에서 떨이 한 데이터까지 다 수신 완료 → 연결 해제
















