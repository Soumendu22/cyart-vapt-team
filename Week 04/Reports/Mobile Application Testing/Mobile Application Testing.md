# Mobile Application Testing Lab – Step-by-Step Guide

## Important Prerequisite: Setting Up the Mobile Testing Environment

Before starting the lab activities, a suitable Android testing environment must be prepared. Since the testing is performed from a Kali VM, a rooted Android emulator is the most effective and flexible approach.

---

## 1. Installing Genymotion Android Emulator

**Theory:**  
An **Android Emulator** is a virtual device that mimics Android hardware and software, allowing security analysts and developers to test mobile applications safely. **Genymotion** is preferred because it integrates well with Kali Linux, supports root access, and runs faster than standard emulators.

**Steps:**
1. Visit the [Genymotion website](https://www.genymotion.com/), create a free account, and download the Personal Use version for Linux.  
2. Install Genymotion along with its required **VirtualBox** dependency.  
3. Launch Genymotion and add a virtual device (e.g., a customizable device running Android 9 or Android 10).  
4. Start the emulator.

---

## 2. Rooting the Emulator

**Theory:**  
Rooting provides **privileged access** to the Android system files and allows tools such as **Frida** and **Drozer** to perform in-depth testing by modifying or accessing protected areas of the OS.

**Steps:**
1. Once the emulator is running, open the Apps drawer.  
2. Drag and drop the `Genymotion-ARM-Translation_v1.1.zip` file onto the emulator window to enable ARM compatibility.  
3. Drag and drop the `SuperSU.zip` file to enable root access.  
4. Reboot the emulator.  
5. Verify root access by confirming the presence of the **SuperSU** application.

---

## 3. Installing Android Debug Bridge (ADB)

**Theory:**  
**Android Debug Bridge (ADB)** is a command-line tool that facilitates communication between a computer and an Android device or emulator. It is used for tasks like installing apps, managing files, and executing shell commands.

**Command:**
```bash
sudo apt update && sudo apt install android-sdk-platform-tools
```

---

## 4. Connecting ADB to the Emulator

**Theory:**  
After setting up ADB, connecting it ensures that the host (Kali) can interact with the emulator for deployment and instrumentation.

**Command:**
```bash
adb devices
```

You should see the emulator listed in the output, confirming a successful connection.

---

# Activity 1: Static Analysis Using MobSF

**Theory:**  
**Static analysis** involves examining an application's code and resources without executing it. **Mobile Security Framework (MobSF)** automates this process by decompiling APKs, analyzing permissions, and checking for insecure coding practices.

---

## 1. Starting MobSF

**Steps:**
```bash
cd /opt/MobSF
sudo ./run.sh
```

Once the server starts, open a browser and navigate to:  
[http://127.0.0.1:8000](http://127.0.0.1:8000)

---

## 2. Obtaining a Test APK

Download `herdprotect-1.5.apk` (OWASP GoatDroid) from the [OWASP GoatDroid releases page](https://github.com/OWASP/OWASP-GoatDroid-Project).  
Save the file to an accessible directory (e.g., `Downloads`).

---

## 3. Uploading and Analyzing the APK

**Steps:**
1. Open the MobSF web interface.  
2. Click **Upload** and select the APK file.  
3. Click **Analyze** to start the static analysis.  
4. MobSF will decompile the application, scan for vulnerabilities, and generate a detailed report.

---

## 4. Documenting the Insecure Storage Finding

**Theory:**  
Insecure storage vulnerabilities occur when apps store sensitive information (like credentials or tokens) in *world-readable* locations such as shared preferences or external storage. Attackers can extract these files to retrieve confidential data.

**Steps:**
1. Review the **Security Score** in the report.  
2. Navigate to the **Vulnerabilities** section.  
3. Identify findings related to **Insecure Data Storage** or **Application Data Backup Enabled**.  
4. Document this finding as it demonstrates improper handling of user data.

---

# Activity 2: Dynamic Testing Using Frida

**Theory:**  
While static analysis focuses on code inspection, **dynamic analysis** monitors and manipulates an app while it runs. **Frida** allows runtime code injection, enabling security testers to override app behavior (e.g., bypassing authentication or SSL pinning).

---

## 1. Installing Frida Server on the Emulator

**Steps:**
1. Check the Frida version on Kali:
   ```bash
   frida --version
   ```
2. Download the matching `android-x86_64` Frida server from the [Frida releases page](https://github.com/frida/frida/releases).  
3. Deploy and run the server:
   ```bash
   mv frida-server-16.x.x-android-x86_64.xz frida-server.xz
   unxz frida-server.xz
   adb push frida-server /data/local/tmp/
   adb shell "chmod 755 /data/local/tmp/frida-server"
   adb shell "/data/local/tmp/frida-server &"
   ```

---

## 2. Installing the Test Application

```bash
adb install herdprotect-1.5.apk
```

---

## 3. Writing a Frida Script to Bypass Authentication

**Theory:**  
Frida scripts use runtime hooks to intercept and modify function behavior. In this task, a script is used to override the `isLoginCorrect` method in the login activity, forcing it to return `true` and simulate successful authentication.

**Script (`bypass.js`):**
```javascript
Java.perform(function () {
    console.log("[*] Starting Frida script to bypass authentication...");

    var MainActivity = Java.use("com.owasp.goatdroid.herdfinancial.activities.LoginActivity");

    MainActivity.isLoginCorrect.implementation = function (username, password) {
        console.log("[+] Hooked isLoginCorrect function!");
        console.log("Arguments: Username=" + username + ", Password=" + password);
        console.log("[-] Bypassing authentication, returning true.");
        return true;
    };
});
```
*Note:* If the function name differs, use `jadx-gui` to inspect the APK and locate the relevant method.

---

## 4. Running the Frida Script

**Steps:**
1. Identify the package name (`com.owasp.goatdroid.herdfinancial`).  
2. Ensure the app is running.  
3. Execute the script:
   ```bash
   frida -U -f com.owasp.goatdroid.herdfinancial -l bypass.js --no-pause
   ```

After starting the app, log in with any credentials — the authentication bypass validates successful runtime manipulation.

---

# Activity 3: IPC Testing Using Drozer

**Theory:**  
**Inter-Process Communication (IPC)** in Android enables components like Activities, Services, and Broadcast Receivers to communicate between apps. **Drozer** helps discover and exploit insecure IPC configurations, such as exported components vulnerable to unauthorized access.

---

## 1. Installing Drozer Agent

**Steps:**
1. Download the Drozer Agent APK from the [Drozer releases page](https://labs.withsecure.com/tools/drozer).  
2. Install it:
   ```bash
   adb install drozer-agent-2.x.x.apk
   ```

---

## 2. Starting Drozer Console

**Steps:**
1. Open the Drozer Agent app and enable it on the emulator.  
2. Forward the communication port and connect from Kali:
   ```bash
   adb forward tcp:31415 tcp:31415
   drozer console connect
   ```
A `dz>` prompt confirms a successful connection.

---

## 3. Enumerating the Attack Surface

**Theory:**  
Drozer allows analysts to map the **attack surface** of Android apps — identifying exported components that can be invoked externally, potentially allowing privilege escalation or data exposure.

**Commands:**
```bash
run app.package.list -f goatdroid
run app.package.attacksurface com.owasp.goatdroid.herdfinancial
```

This lists exported activities, services, and receivers accessible to other apps.

---

## 4. Exploiting an Exposed Activity

**Theory:**  
An exposed activity without proper authentication can be launched directly by an attacker, bypassing intended access restrictions.

**Commands:**
```bash
run app.activity.info -a com.owasp.goatdroid.herdfinancial
```

Identify sensitive activities (e.g., home or balance views) that may be directly launched.

---

# Conclusion

This lab demonstrates a complete **mobile application security testing workflow**, integrating three critical methods:

- **Static Analysis (MobSF):** Code-level vulnerability discovery  
- **Dynamic Analysis (Frida):** Runtime manipulation and testing  
- **IPC Testing (Drozer):** Inter-app communication analysis  

Together, these techniques expose insecure coding practices and misconfigured Android components that can lead to significant security vulnerabilities.
