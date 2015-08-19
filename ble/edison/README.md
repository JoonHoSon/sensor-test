# Intel edison에서 Bluethooth 활성화 방법
```bash
$ rfkill unblock bluetooth
$ hciconfig hci0 up
$ rfkill list
```

`rfkill list`명령어의 실행 결과가 다음과 같으면 성공입니다.
![bluetooth 활성화 결과](https://docs.google.com/uc?id=0B02RRVY3KrmeV2d0VVBUZTkxVDg)

# Intel edison gatttool 설치방법
에디슨에는 gatttool이 설치되어 있지 않습니다. 또한 opkg로 bluez를 설치해도 gatttool은 포함되어 있지 않습니다.[^ref1]  
따라서, 아래의 과정을 통해 gatttool을 설치합니다.

## 소스 다운로드
```bash
$ wget --no-check-certificate https://www.kernel.org/pub/linux/bluetooth/bluez-5.24.tar.xz
```

## 압축 해제
만약 xz 압축 도구가 설치되어 있지 않을 경우 다음의 명령어로 설치합니다.

```bash
$ opkg install xz
```

다운로드 받은 소스를 압축 해제 합니다.

```bash
$ xz -d bluez-5.24.tar.xz
$ tar xvf bluez-5.24.tar
$ cd bluez-5.24
```

### 빌드 및 설치
```bash
$ make && make install
```

gatttool 복사
```bash
$ cp attrib/gatttool /usr/bin
```

[^ref1]: [기술 여행자 블로그](http://arsviator.blogspot.kr/2015/03/gatttool-install-gatttool-in-intel.html) 및 [Intel](https://software.intel.com/en-us/articles/using-the-generic-attribute-profile-gatt-in-bluetooth-low-energy-with-your-intel-edison) 참고