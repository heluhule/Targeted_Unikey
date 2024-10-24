# Targeted_Unikey

This repository explores the **Portable Executable (PE) Injection** technique. The project focuses on code injection methods, bypassing static analysis, and leveraging Windows features for stealth and persistence.

⚠️ **Disclaimer**: This project is for educational purposes only. The techniques demonstrated here should **never** be used for malicious purposes. Always conduct testing in a safe, legal, and controlled environment.

---

## 🗂 Project Overview

The aim is to learn **PE injection** by modifying headers, accessing Windows APIs directly from memory, and experimenting with native features to maintain stealth. Below is a breakdown of the core techniques used.

---

## 📌 Features

### 1. **Delta Technique for PE Injection**

The **Delta Technique** ensures proper alignment when injecting malicious code into other PE files without disrupting the host's original functionality.

- The **PE Header** is modified to accommodate the new code and align the **EntryPoint** correctly.
- Using the delta offset ensures the injected code integrates seamlessly into the host, preserving normal operation.

This method ensures that any injected code executes correctly without raising suspicion during runtime.

---

### 2. **Bypassing Static Analysis through API Access**

To avoid detection by static analysis tools, we **bypassed direct library imports**:

- Instead of importing libraries (e.g., kernel32.dll), we accessed **Windows APIs** directly through memory.
- This method avoids leaving suspicious function imports in the PE Header, making our code harder to detect.

By locating and using API functions dynamically, the injection becomes more resilient to static detection mechanisms.

---

### 3. **Windows Features Exploitation**

We leveraged several **Windows features** to achieve stealthy code execution:

- **Hidden Files and Shortcuts:**  
  - Payloads were stored as hidden files to reduce their visibility.
  - Shortcut (.lnk) files were used to execute commands silently, avoiding user suspicion.

- **Run Registry Modification:**  
  - Rather than writing to the Run Registry directly (which is easily detected), we injected code into legitimate programs.
  - **UnikeyNT**, a commonly used typing tool in Vietnam, was chosen due to its convenient startup configuration via a checkbox option.

These methods demonstrate how legitimate Windows features can be manipulated for malicious purposes while maintaining persistence.

---

### 4. **Self-Deleting Batch File Execution**

We employed **self-deleting batch scripts** to erase traces after executing the main payload:

- A batch file is created to run the payload and delete itself upon completion.
- This minimizes the digital footprint, making it harder for investigators to find evidence on the compromised system.

This technique ensures stealth by covering tracks during the execution process.

---

## 🚀 How it Works

1. **PE Injection:**  
   - Identify and modify the PE Header using the Delta Technique to inject malicious code.

2. **Bypass Library Imports:**  
   - Access essential API functions directly from memory to avoid detection by static analysis tools.

3. **Windows Feature Exploitation:**  
   - Utilize hidden files, shortcuts, and registry modifications to maintain persistence.

4. **Self-Deleting Batch Execution:**  
   - Use batch scripts that delete themselves after execution to minimize traces.

https://github.com/user-attachments/assets/fa2b801c-5fcd-4e91-8c5f-376b1f88e068

---

⚠️ ⚠️ ⚠️ As the video shown, the code is a bit noisy since it pops up some console with some lines. This is easy too handle just by an argument but I'm too lazy to do just a change and retest it again! What's more, the C file is also not really necessary, but writing stuff in ASM takes too long so I just decided to write C or Python for the last part...
