# SHAOSE — Windows File Surgeon, Unlocker & Security Station (v1.0.1.0)

SHAOSE is a native, privacy-focused Windows file management, handle unlocking, security inspection, and recovery suite built with .NET 10 LTS and WPF.

## 📋 Publisher & Architecture Overview

* **Publisher / Developer:** ALLAHVERDİ CAN
* **Microsoft Store Package Identity:** `ALLAHVERDCAN.SHAOSE`
* **Publisher ID:** `CN=80F86ABB-4ABB-4524-A032-0CE77FF05712`
* **Package Version:** `1.0.1.0`
* **Architecture:** Windows 10 / Windows 11 x64 Native Desktop Application (.NET 10 LTS, UseWPF=true)
* **Official YouTube Channel:** [ALLAHVERDİ CAN](https://www.youtube.com/@ALLAHVERDICAN)

---

## ⚙️ Technical Overview & Surgical Modules

### 🎯 The Resonance Drop Pod (Smart Drag & Drop Triage)

Drag and drop any locked file, long-path folder, suspicious executable, or damaged archive directly onto the centerpiece orb. SHAOSE performs a 4-stage local diagnostic (RestartManager handle inspection, extended path length check, SHA-256 & Shannon entropy calculation, and header verification) and routes to the appropriate surgical module.

### 🔓 Module 1 — Force Unlocker, Shredder & Long-Path (\?) Surgeon

* Queries the official Windows Restart Manager API (rstrtmgr.dll) to identify processes holding open handles on a file or folder.
* Verifies process identity and StartTime (TOCTOU PID-reuse protection) while strictly safeguarding Session-0 and critical Windows processes (System, csrss, lsass, dwm, svchost, explorer) and protected root directories.
* Supports safe Recycle Bin deletion (SHFileOperation with FOF_ALLOWUNDO) and 3-pass cryptographic shredding (0x00, 0xFF, random bytes + MFT filename obfuscation) using extended-length Win32 paths (\?) to remove 260+ character Path Too Long structures without following symbolic links or junctions.

### 🛡️ Module 2 — Isolated Threat Shield, Authenticode, Entropy & Manual Eradication

* Executes on-demand, isolated single-file or folder scans via the local Microsoft Defender CLI engine (MpCmdRun.exe -Scan -ScanType 3 -File) without slowing down the entire system.
* Computes stream-based MD5, SHA-1, and SHA-256 digests, calculates Shannon byte entropy (0.00–8.00 bits/byte), inspects PE32/PE64 headers, and validates X.509 Authenticode digital signatures.
* **Manual Threat Eradication:** When a threat is detected or a suspicious file needs removal, the user can explicitly trigger local secure deletion (3-pass shredding) or Recycle Bin transfer directly from the security interface.

### 🧹 Module 3 — Deep Program Uninstaller & Orphan Leftover Hunter

* Enumerates installed desktop programs across 64-bit and 32-bit HKLM and HKCU Uninstall registry hives.
* Safely parses UninstallString executables and arguments without invoking cmd.exe (eliminating command injection risks).
* Scans %APPDATA%, %LOCALAPPDATA%, and %PROGRAMDATA% for inactive orphan leftover folders and moves selected items to the Windows Recycle Bin.

### 🗜️ Module 4 — Damaged Archive Forced Extractor & Streaming Media Header Doctor

* Salvages intact files from CRC-damaged or truncated .zip, .docx, .xlsx, and .pptx archives with strict Zip-Slip path traversal protection and a stream-based PK\x03\x04 local header carver fallback.
* Repairs corrupted JPEG (FF D8 FF SOI / FF D9 EOI), PNG (89 50 4E 47), and MP4/MOV (ftyp atom) headers using 64 KB streaming I/O so multi-gigabyte files never cause high memory usage.

---

## 🔒 Privacy Policy / Gizlilik Politikası

* **Effective Date / Yürürlük Tarihi:** November 2026
* **Application Name / Uygulama Adı:** SHAOSE (`ALLAHVERDCAN.SHAOSE`)
* **Publisher / Yayıncı:** ALLAHVERDİ CAN (`CN=80F86ABB-4ABB-4524-A032-0CE77FF05712`)

### 1. Zero Data Collection & 100% Local Processing (English)

* **No Personal Data Collected:** SHAOSE does not collect, transmit, store, rent, or share any personal information, files, file names, cryptographic hashes, directory structures, hardware identifiers, IP addresses, or usage telemetry.
* **100% Offline Execution & Local Eradication:** All file handle unlocking (rstrtmgr.dll), file shredding, cryptographic hashing (MD5/SHA-1/SHA-256), isolated Microsoft Defender scanning (MpCmdRun.exe), program uninstallation, and user-initiated file deletion/Recycle Bin operations run 100% locally on the user's Windows device.
* **No Cloud or Third-Party SDKs:** SHAOSE contains zero third-party analytics SDKs, zero advertising trackers, and zero background network services. The only external link is the optional button that opens the developer's official YouTube channel ([https://www.youtube.com/@ALLAHVERDICAN](https://www.youtube.com/@ALLAHVERDICAN)) in the user's default web browser when explicitly clicked by the user.
* **Local Diagnostic Logs:** Recoverable diagnostic events are written exclusively to the local folder %LOCALAPPDATA%\SHAOSE_Data\shaose_diagnostics.log (capped at 512 KB with automatic rotation), with user profile paths sanitized as %USERPROFILE%. These logs never leave your device.

### 2. Sıfır Veri Toplama ve %100 Yerel Çalışma İlkeleri (Türkçe)

* **Kişisel Veri Toplanmaz:** SHAOSE hiçbir kişisel veriyi, dosya içeriğini, dosya adını, kriptografik özeti, klasör yapısını, donanım kimliğini veya kullanım istatistiğini toplamaz, saklamaz, uzak bir sunucuya göndermez ve üçüncü taraflarla paylaşmaz.
* **%100 Çevrimdışı (Offline) Mimari ve Yerel Silme:** Kilit kırma (rstrtmgr.dll), güvenli dosya parçalama, kriptografik özet hesaplama (MD5/SHA-1/SHA-256), izole Microsoft Defender taraması (MpCmdRun.exe), program kaldırma ve kullanıcının isteğiyle tetiklenen yerel dosya silme/geri dönüşüm işlemleri tamamen %100 yerel olarak kullanıcının kendi bilgisayarında gerçekleşir.
* **Üçüncü Taraf İzleyici Yoktur:** Uygulama içinde hiçbir reklam ağı, analitik kütüphanesi veya arka plan internet bağlantısı bulunmaz. Yalnızca kullanıcı kendi isteğiyle üst bardaki YouTube butonuna tıkladığında varsayılan tarayıcıda geliştiricinin resmi YouTube kanalı ([https://www.youtube.com/@ALLAHVERDICAN](https://www.youtube.com/@ALLAHVERDICAN)) açılır.
* **Yerel Hata Günlüğü:** Olası uygulama içi tanı kayıtları %USERPROFILE% maskelemesiyle yalnızca kullanıcının bilgisayarındaki %LOCALAPPDATA%\SHAOSE_Data\shaose_diagnostics.log dosyasında (512 KB sınırıyla) tutulur ve cihaz dışına asla çıkmaz.

---

## 📞 Contact / İletişim

* **Publisher / Yayıncı:** ALLAHVERDİ CAN
* **Official Channel / Resmi Kanal:** [https://www.youtube.com/@ALLAHVERDICAN](https://www.youtube.com/@ALLAHVERDICAN)
