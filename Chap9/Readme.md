
1. c:\사용자 \ [현재계정]
2. 오른클릭하여 빈 .wslconfig.txt 만들기
3. 메모장으로 .wslconfig.txt를 열고 아래 내용 복사후 저장
<img width="386" height="347" alt="image" src="https://github.com/user-attachments/assets/99b857d0-6afd-42b7-9714-ad8c670465b0" />

```shell
[wsl2]
networkingMode=mirrored
firewall=false
```
4. f2키 눌러서 .wslconfig.txt -> .wslconfig 로 변경
5. powershell(관리자모드) 에서 wsl --shutdown 입력
6. powershell(관리자모드) 에서 netsh advfirewall set allprofiles state off 입력하여 방화벽을 끄기
7. powershell(관리자모드) 에서 wsl 입력
8. wsl 안에서 ifconfig 확인


#수업마친후 할일

powershell(관리자모드) 에서 netsh advfirewall set allprofiles state on 입력하여 방화벽을 켜기**


----------------------------------------------
# 방화벽 문제 해결

```shell
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 topic list
/parameter_events
/rosout
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 daemon stop
The daemon has been stopped
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 topic list
^Cuser@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ echo $ROS_DOMAIN_ID
30
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 topic list
^Cuser@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 daemon start
The daemon has been started
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 topic list
/parameter_events
/rosout
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ exit
logout
PS C:\WINDOWS\system32> netsh advfirewall set allprofiles state off
확인됨

PS C:\WINDOWS\system32> wsl --shutdwon
잘못된 명령줄 인수: --shutdwon
지원되는 인수 목록을 가져오려면 'wsl.exe --help' 사용하세요.
PS C:\WINDOWS\system32> wsl --shutdown
PS C:\WINDOWS\system32> wsl
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ export ROS_DOMAIN_ID=30
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 daemon start
The daemon has been started
user@DESKTOP-FUDPTFE:/mnt/c/WINDOWS/system32$ ros2 topic list
/cmd_vel
/joint_states
/odom
/parameter_events
/robot_description
/rosout
/scan
/tf
/tf_static

```
