# Nmap




# SNMP
### SNMPWALK
```bash
$ snmpwalk -c public -v2c 10.10.10.116                                                
iso.3.6.1.2.1.1.1.0 = STRING: "Hardware: AMD64 Family 23 Model 1 Stepping 2 AT/AT COMPATIBLE - Software: Windows Version 6.3 (Build 15063 Multiprocessor Free)"                               
iso.3.6.1.2.1.1.2.0 = OID: iso.3.6.1.4.1.311.1.1.3.1.1                                 
iso.3.6.1.2.1.1.3.0 = Timeticks: (691083) 1:55:10.83                                           
iso.3.6.1.2.1.1.4.0 = STRING: "IKE VPN password PSK - 9C8B1A372B1878851BE2C097031B6E43"      
iso.3.6.1.2.1.1.5.0 = STRING: "Conceal" 
```
"IKE VPN password PSK - 9C8B1A372B1878851BE2C097031B6E43"   

9C8B1A372B1878851BE2C097031B6E43:NTLM:Dudecake1!
![[Pasted image 20211128103121.png]]

### SNMP-CHEK
```bash
snmp-check 10.10.10.116
```

```bash
[*] TCP connections and listening ports:                                                                                                                                            [212/1501]
                                                                                                                                                                                              
  Local address         Local port            Remote address        Remote port           State                                                                                               
  0.0.0.0               21                    0.0.0.0               0                     listen                                                                                              
  0.0.0.0               80                    0.0.0.0               0                     listen              
  0.0.0.0               135                   0.0.0.0               0                     listen              
  0.0.0.0               445                   0.0.0.0               0                     listen              
  0.0.0.0               49664                 0.0.0.0               0                     listen              
  0.0.0.0               49665                 0.0.0.0               0                     listen              
  0.0.0.0               49666                 0.0.0.0               0                     listen              
  0.0.0.0               49667                 0.0.0.0               0                     listen              
  0.0.0.0               49668                 0.0.0.0               0                     listen              
  0.0.0.0               49669                 0.0.0.0               0                     listen              
  0.0.0.0               49670                 0.0.0.0               0                     listen              
  10.10.10.116          139                   0.0.0.0               0                     listen
```

```bash
[*] Listening UDP ports:                                                                                                                                                                      
                                                                                                                                                                                              
  Local address         Local port                                                                                                                                                            
  0.0.0.0               123 (NTP)                                                                                                                                                                   
  0.0.0.0               161 (SNMP)                                                                                                                                                                  
  0.0.0.0               500 (IPSEC IKE - will Abuse)                                                                                                                                                                  
  0.0.0.0               4500(IPSEC ISAKMP - will Abuse)                                                                                                                                                                 
  0.0.0.0               5050 (Unknow)                                                                                                                                                                 
  0.0.0.0               5353 (mDNS)                                                                                                                                                                 
  0.0.0.0               5355 (LLMNR)                                                                                                                                                                 
  10.10.10.116          137  (SMB)                                                                                                                                                                 
  10.10.10.116          138  (SMB)                                                                                                                                                                 
  10.10.10.116          1900 (UPNP)                                                                                                                                                                
  10.10.10.116          58617 (?)                                                                                                                                                                
  127.0.0.1             1900  (UPNP)                                                                                                                                                                
  127.0.0.1             58618 (?)
```

### IKE-SCAN
VPN config
```bash
$ sudo ike-scan -M 10.10.10.116 -s 0
Starting ike-scan 1.9.4 with 1 hosts (http://www.nta-monitor.com/tools/ike-scan/)
10.10.10.116    Main Mode Handshake returned
        HDR=(CKY-R=f624bef629852e39)
        SA=(Enc=3DES Hash=SHA1 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration(4)=0x00007080)
        VID=1e2b516905991c7d7c96fcbfb587e46100000009 (Windows-8)
        VID=4a131c81070358455c5728f20e95452f (RFC 3947 NAT-T)
        VID=90cb80913ebb696e086381b5ec427b1f (draft-ietf-ipsec-nat-t-ike-02\n)
        VID=4048b7d56ebce88525e7de7f00d6c2d3 (IKE Fragmentation)
        VID=fb1de3cdf341b7ea16b7e5be0855f120 (MS-Negotiation Discovery Capable)
        VID=e3a5966a76379fe707228231e5ce8652 (IKE CGA version
```

        HDR=(CKY-R=f624bef629852e39)
        SA=(
		Enc=3DES 
		Hash=SHA1 
		Group=2:modp1024 
		Auth=PSK (Dudecake1!)
		LifeType=Seconds 
		LifeDuration(4)=0x00007080) (28800 seconds = 8hours)
        