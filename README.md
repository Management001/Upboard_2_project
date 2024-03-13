# CSI 툴킷 관련 문제 해결…. (1)

### 사용 및 설치할 툴킷

---

https://github.com/FIVEYOUNGWOO/IEEE-802.11n-CSI-Camera-Synchronization-Toolkit

### 사용되는 우분투 버전

---

**18.04.0**

### 필요한 커널 버전

---

**4.15.0-213-general**

### **(1). Kernel version:**

---

Before proceeding further, you need to check the version of your kernel. It should be **4.15**, otherwise, the commands below won't work. The following command will print that information:

```jsx
uname -r
```

> **No Problem… !**
> 

### **(2). First download the essential packages:**

---

```
sudo apt-get install build-essential linux-headers-$(uname -r) git-core
```

> **No Problem… !**
> 

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

> **No Problem… !**
> 

```jsx
sudo apt-get update
```

> **No Problem… !**
> 

*** If you don't need to install this gcc version, skip the below line :)

```
sudo apt-get install gcc-8 g++-8
```

> **No Problem… !**
> 

```
sudo apt-get install libgtk2.0-dev
```

> **No Problem… !**
> 

```
sudo apt-get install pkg-config
```

> **No Problem… !**
> 

```
sudo apt-get install cmake
```

> **No Problem… !**
> 

```jsx
sudo apt update
```

> **No Problem… !**
> 

### **(3). Check the GCC version:**

---

```
ls -l /usr/bin/gcc /usr/bin/g++
```

> **No Problem… !**
> 

**Now change the version of gcc/g++ to version 8:**

```jsx
sudo rm /usr/bin/gcc
```

> **No Problem… !**
> 

```jsx
sudo rm /usr/bin/g++
```

> **No Problem… !**
> 

```jsx
sudo ln -s /usr/bin/gcc-8 /usr/bin/gcc
```

> **No Problem… !**
> 

```jsx
sudo ln -s /usr/bin/g++-8 /usr/bin/g++
```

> **No Problem… !**
> 

### **(4). Build and install the modified wireless LAN driver:**

---

```
sudo apt-get install gcc make linux-headers-$(uname -r) git-core
```

> **No Problem… !**
> 

```
CSITOOL_KERNEL_TAG=csitool-$(uname -r | cut -d . -f 1-2)
```

> **No problem… but that doesn't need to be done.… !
위 명령어는 환경설정 작업을 의미하며, https://github.com/spanev/linux-80211n-csitool 사이트의 파일에서만 동작합니다.**
> 

```
git clone https://github.com/FIVEYOUNGWOO/IEEE-802.11n-CSI-Camera-Synchronization-Toolkit.git
```

> **No Problem… !**
> 

```
cd IEEE-802.11n-CSI-Camera-Synchronization-Toolkit/linux-80211n-csitool
```

> **No Problem… !**
> 

```
git checkout ${CSITOOL_KERNEL_TAG}
```

> **Do not work… !
해당 명령어는  https://github.com/spanev/linux-80211n-csitool 사이트의 파일을 기반으로, 해당 repository의 ‘csitool-4.15’ tag가 존재해야만 동작합니다.**
> 

```
make -C /lib/modules/$(uname -r)/build M=$(pwd)/drivers/net/wireless/iwlwifi modules
```

> **Do not work… ! 
<중요> 해당 문제를 해결하기 위해 근본이 되는 `linux-80211n-csitool/drivers/net/wireless/intel/iwlwifi` 의 모든 파일을 기존 `IEEE-802.11n-CSI-Camera-Synchronization-Toolkit/linux-80211n-csitool/drivers/net/wireless/iwlwifi` 으로 덮어쓰기를 해야합니다.**
> 

```
sudo make -C /lib/modules/$(uname -r)/build M=$(pwd)/drivers/net/wireless/iwlwifi INSTALL_MOD_DIR=updates
```

> **No Problem… !
이전 작업에서 ‘파일 덮어쓰기’ 이후에 실행하여야 정상적으로 컴파일됩니다.**
> 

### (5). Install the Modified firmware:

---

```
for file in /lib/firmware/iwlwifi-5000-*.ucode; do sudo mv $file $file.orig; done
```

> **No Problem… !**
> 

```
sudo cp IEEE-802.11n-CSI-Camera-Synchronization-Toolkit/supplementary/firmware/iwlwifi-5000-2.ucode.sigcomm2010 /lib/firmware/
```

> **No Problem… !
해당 명령어를 정상적으로 실행하기 위해 경로를 ‘home’ 위치로 바꾸어야 합니다.**
> 

```jsx
sudo ln -s iwlwifi-5000-2.ucode.sigcomm2010 /lib/firmware/iwlwifi-5000-2.ucode
```

> **No Problem… !**
> 

### **(6). Build the userspace logging tool:**

---

```
make -C IEEE-802.11n-CSI-Camera-Synchronization-Toolkit/supplementary/netlink
```

> **No Problem… !
해당 명령어를 정상적으로 실행하기 위해 경로를 ‘home’ 위치로 바꾸어야 합니다.**
> 

### **(7). Unzip OpenCV to utilize the USB camera:**

---

```
cd IEEE-802.11n-CSI-Camera-Synchronization-Toolkit/camera_tool
```

> **No Problem… !**
> 

```
unzip opencv-2.4.13.6.zip
```

> **No Problem… !
’A’를 눌러 전부 압축을 해제합니다.**
> 

```jsx
cd opencv-2.4.13.6/install
```

> **No Problem… !**
> 

### **(8). Compile and install OpenCV:**

---

```
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
```

> **No Problem… !**
> 

```
cmake ..
```

> **No Problem… !**
> 

```
make
```

> **No Problem… !**
> 

```
sudo make install
```

> **No Problem… !**
> 

### **(9). Configuration OpenCV:**

---

```jsx
sudo gedit /etc/ld.so.conf.d/opencv.conf
```

> **No Problem… !
해당 명령어를 실행하면 gedit창이 나타납니다.**
> 

***** opencv.conf 메모장에 해당 내용을 첨부합니다.**

```jsx
**/usr/local/lib**
```

> **No Problem… !
메모장에 작성 후 저장하십시오.**
> 

```
sudo ldconfig
```

> **No Problem… !**
> 

```jsx
sudo gedit /etc/bash.bashrc
```

> **No Problem… !
해당 명령어를 실행하면 gedit창이 나타납니다.**
> 

***** bash.bashrc 메모장 최하단에 해당 내용을 첨부합니다.**

```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
export PKG_CONFIG_PATH
```

> **No Problem… !
메모장에 작성 후 저장하십시오.**
> 

```jsx
sudo reboot
```

> **No Problem… !**
> 

### **(10). Compile user-application:**

---

```
cd IEEE-802.11n-CSI-Camera-Synchronization-Toolkit/supplementary/netlink
```

> **No Problem… !**
> 

```
sudo gedit /etc/ld.so.conf.d/opencv.conf
```

> **No Problem… !**
> 

***** opencv.conf 메모장에 해당 내용을 첨부합니다.**

```jsx
**/usr/local/lib**
```

> **No Problem… !
메모장에 작성 후 저장하십시오.**
> 

```
make
```

> **No Problem… !**
>
