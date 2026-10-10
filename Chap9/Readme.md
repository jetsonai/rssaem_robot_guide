
1. c:\사용자\[현재계정]
2. 오른클릭하여 빈 .wslconfig.txt 만들기
3. 메모장으로 .wslconfig.txt를 열고 아래 내용 복사후 저장
<img width="386" height="347" alt="image" src="https://github.com/user-attachments/assets/99b857d0-6afd-42b7-9714-ad8c670465b0" />

```shell
[wsl2]
networkingMode=mirrored
firewall=false
```
4. f2키 눌러서 .wslconfig.txt -> .wslconfig 로 변경
5. powershell 에서 wsl --shutdown 입력
6. powershell 에서 wsl 입력
7. wsl 안에서 ifconfig 확인
