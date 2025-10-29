# Software Reversing and Exploitation: Minor Project

> Comprehensive vulnerability analysis and exploitation across Linux (ELF) and Windows (PE32) binaries, demonstrating mastery of static/dynamic analysis, memory corruption, and automated exploit development.

**Final project for the Software Reversing and Exploitation (SRE) Minor**  
The Hague University of Applied Sciences | June 2024

## 🎯 Core Technical Competencies

| Skill Domain | Demonstrated Techniques |
|--------------|------------------------|
| **Dynamic Analysis** | GDB-PEDA and x32dbg for live memory inspection, register manipulation, and runtime flow analysis |
| **Exploitation** | Command Injection, Stack-based Buffer Overflows, SEH exploitation, Format String vulnerabilities |
| **Defense Evasion** | CANARY bypass, ASLR circumvention, return address redirection, integer overflow exploitation |
| **Architecture Mastery** | Deep understanding of CPU/Stack/Heap relationships at Assembly level, little-endian format handling |
| **Automation** | Custom Python fuzzer (`myAutoFuzzExploit.py`) with Pwntools integration for automated vulnerability discovery |

---

## 📁 Repository Structure
```
.
├── HasanCoskun_SoftwareReversing_Final.pdf    # Complete technical write-up (45 pages)
│
├── Linux-Challenges/
│   ├── dungeon1/                              # Command Injection exploit
│   ├── dungeon3/                              # Buffer Overflow with precise offset calculation
│   ├── dungeon4/                              # Format String vulnerability
│   └── dungeon5/                              # CANARY bypass + Buffer Overflow combo
│
├── Windows-Exploits/
│   ├── challenge1/                            # Integer Overflow → Buffer Overflow chain
│   ├── challenge3/                            # PATH environment variable exploitation
│   ├── windows6/                              # Structured Exception Handling (SEH) exploit
│   ├── modern2/                               # Automated Format String exploitation
│   └── modern3/                               # Magic String brute-force attack
│
└── Tools/
    └── myAutoFuzzExploit.py                   # Automated fuzzer & exploit generator
```

---

## 🛠️ Featured Tool: myAutoFuzzExploit.py

A sophisticated automated vulnerability scanner and exploit generator with intelligent decision-making:

### Core Capabilities
- ✅ **Command Injection Detection**: Tests shell symbols (`|`, `&`, `$()`, `;`, `&&`, `'`)
- ✅ **Automated Flag Extraction**: Attempts to read `flag.txt`, `password.txt`, `secret.txt`
- ✅ **Buffer Overflow Analysis**: Calculates precise Return Address offsets via GDB integration
- ✅ **Function Discovery**: Identifies hidden functions (e.g., `vault`) using GDB automation
- ✅ **Payload Generation**: Creates exploit payloads with proper padding and address manipulation

### Workflow
```python
1. Test for Command Injection vulnerabilities
   ├─ If found → Attempt flag extraction
   └─ If not found → Proceed to Buffer Overflow testing
       ├─ Analyze functions with GDB
       ├─ Calculate offset (padding to return address)
       ├─ Identify target function address
       └─ Generate and execute payload
```

### Key Features
- Fully documented Python code with error handling
- Integrates Pwntools for binary manipulation
- GDB automation for dynamic analysis
- Supports both Linux (ELF) and Windows (PE32) binaries

---

## 📊 Challenge Breakdown

### Linux Exploitation Journey

| Challenge | Vulnerability Type | Key Technique |
|-----------|-------------------|---------------|
| **dungeon1** | Command Injection | Pipe operator (`\|`) to chain commands |
| **dungeon3** | Buffer Overflow | 40-byte offset calculation, return address overwrite |
| **dungeon4** | Format String | ASLR bypass via `%p` specifier, fruit name extraction |
| **dungeon5** | CANARY + Buffer Overflow | Leak canary with `%15$p`, reconstruct payload |

### Windows Exploitation Journey

| Challenge | Vulnerability Type | Key Technique |
|-----------|-------------------|---------------|
| **Windows 1** | Integer Overflow | Trigger overflow with `-1` or max value |
| **Windows 3** | PATH Hijacking | Replace `cmd.bat` in execution path |
| **Windows 6** | SEH Exploitation | Pop-Pop-Ret method, NOP sled to shellcode |
| **modern2** | Format String | Hex-to-ASCII conversion, endianness handling |
| **modern3** | Magic String | Brute-force 40-character buffer with special handling |

---

## 🔬 Technical Highlights

### Memory Protection Bypass
- **CANARY**: Leaked via format string (`%15$p`), reconstructed in payload
- **ASLR**: Circumvented using GDB breakpoints and relative addressing
- **NX**: Worked around using Return-Oriented Programming (ROP) chains

### Assembly-Level Analysis
```assembly
# Example: dungeon5 CANARY structure
[Padding: 72 bytes] + [Canary: 8 bytes] + [RBP: 8 bytes] + [Return Address: 8 bytes]
```

### Exploitation Pattern
```python
# Universal exploit structure
payload = padding + leaked_canary + rbp_padding + target_function_address
```

---

## 📄 Documentation

The complete 45-page technical report (`HasanCoskun_SoftwareReversing_Final.pdf`) includes:

- **Chapter 1**: Tool setup and environment configuration (GDB-PEDA, x32dbg, Snowman)
- **Chapter 2**: Early-stage challenges (basic buffer overflows, command injection)
- **Chapter 3**: Advanced exploitation (format strings, CANARY bypass, SEH)
- **Chapter 4**: Automation and modern techniques (fuzzing, brute-force attacks)

### Key Sections
- Step-by-step vulnerability analysis with annotated assembly code
- Memory layout diagrams and register state visualizations
- Detailed exploit development methodologies
- Screenshots of successful flag captures

---

## 🎓 Learning Outcomes

### Security Concepts Mastered
- Input validation failures and their exploitation vectors
- Memory corruption vulnerabilities (stack/heap)
- Defense mechanism bypass techniques
- Secure coding practices and mitigation strategies

### Practical Skills Acquired
- Binary analysis with multiple toolsets (GDB, x32dbg, Snowman)
- Python scripting for automation and exploit development
- Cross-platform exploitation (Linux ELF vs Windows PE32)
- Debugging and reverse engineering workflows

---

## ⚠️ Disclaimer

**All content in this repository is strictly for educational and ethical security research purposes.**

This project was completed as part of an accredited academic program at The Hague University of Applied Sciences. The techniques demonstrated:
- Should **only** be used in controlled environments
- Require **proper authorization** before testing on any system
- Are intended to **improve defensive security** knowledge
- Must comply with local laws and ethical guidelines

Unauthorized access to computer systems is illegal. This repository serves as a portfolio demonstration of academic research.

---

## 🎓 Academic Context

- **Institution**: The Hague University of Applied Sciences
- **Program**: Software Reversing and Exploitation Minor
- **Student**: Hasan Coşkun (ID: 23169575)
- **Completion Date**: June 2024

---

## 🔗 Additional Resources

- **Full Technical Report**: [HasanCoskun_SoftwareReversing_Final.pdf](./HasanCoskun_SoftwareReversing_Final.pdf)
- **Automation Script**: [myAutoFuzzExploit.py](./Tools/myAutoFuzzExploit.py)

---

## 📧 Contact

For academic inquiries, collaboration on security research, or questions about the methodologies used:
- **GitHub**: [@iamhasancoskun](https://github.com/iamhasancoskun)
- **Project Repository**: [Software_Reversing](https://github.com/iamhasancoskun/Software_Reversing)

---

<p align="center">
  <i>This project demonstrates the importance of understanding offensive security techniques to build better defenses.</i>
</p>
