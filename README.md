# 🪟 C++ Setup in Visual Studio Code on Windows (MinGW + VS Code)

This guide provides step-by-step instructions to install and configure **C++** development in **VS Code** on **Windows** using the **MinGW** compiler.


## 📦 Step 1: Install MinGW Compiler

### 1.1 Download MinGW
- Visit: [https://sourceforge.net/projects/mingw/](https://sourceforge.net/projects/mingw/)
- Click **Download** and run the installer.

### 1.2 Install Required Packages
During installation, select the following components:
- `mingw32-base`
- `mingw32-gcc-g++`

Then click:
- Installation → Apply Changes → Apply

By default, it installs to:  
```
C:\MinGW
```


## ⚙️ Step 2: Add MinGW to System PATH

### 2.1 Open Environment Variables
- Press `Win + S` and search for **Environment Variables**
- Click **"Edit the system environment variables"**
- In the System Properties window, click **"Environment Variables"**

### 2.2 Add Path
- Under **System Variables**, find `Path` → Edit → New
- Add the following:
```
C:\MinGW\bin
```
- Click OK and close all dialogs.

### 2.3 Verify
Open **Command Prompt** and type:
```bash
g++ --version
```

If successful, you’ll see the installed version of g++.



## 🖥 Step 3: Install Visual Studio Code

- Download from: [https://code.visualstudio.com/](https://code.visualstudio.com/)
- Install and open VS Code.



## 🧩 Step 4: Install VS Code Extensions

In VS Code, open Extensions (`Ctrl + Shift + X`) and install:
- ✅ `C/C++` by Microsoft
- ▶️ `Code Runner` *(optional for quick execution)*



## 📁 Step 5: Create and Run a C++ Program

### 5.1 Create a Project Folder

In Command Prompt or VS Code Terminal:

```bash
mkdir CppProject
cd CppProject
code .
```

### 5.2 Create `main.cpp`

Inside VS Code, create a new file called `main.cpp` and paste:

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, C++ in VS Code!" << endl;
    return 0;
}
```



## 🛠 Step 6: Compile and Run

### Option 1: Using Terminal

Open Terminal in VS Code (`Ctrl + ~`) and run:

```bash
g++ main.cpp -o main.exe
./main.exe
```

### Option 2: Using Code Runner (if installed)

- Right-click in the editor → Run Code  
or  
- Press `Ctrl + Alt + N`



## ⚙️ Optional: Add Build Task (Automation)

To build using `Ctrl + Shift + B`:

### 6.1 Create `.vscode/tasks.json`

Go to your project folder and create:

```plaintext
.vscode/tasks.json
```

Paste:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "build and run",
      "type": "shell",
      "command": "g++",
      "args": ["main.cpp", "-o", "main.exe", "&&", "main.exe"],
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "problemMatcher": ["$gcc"]
    }
  ]
}
```

### 6.2 Run with Shortcut

Now press:
```bash
Ctrl + Shift + B
```

Your C++ code will compile and run automatically.


## ✅ Setup Complete!

You are now ready to write, compile, and run C++ code in VS Code on Windows using MinGW.



## 🧰 Useful Commands

```bash
g++ main.cpp -o main.exe   # Compile
./main.exe                 # Run
g++ --version              # Check compiler version
```



## 📝 Notes

- Always save files with `.cpp` extension.
- Make sure `C:\MinGW\bin` is in your PATH.



## 📚 References

- [MinGW Installer](https://sourceforge.net/projects/mingw/)
- [VS Code](https://code.visualstudio.com/)
- [C/C++ VS Code Docs](https://code.visualstudio.com/docs/languages/cpp)
