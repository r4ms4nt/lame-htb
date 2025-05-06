# Lame - Hack The Box (HTB)

![Logo](./capturas/logo_r4ms4nt_circular.png)

**Lame** fue la **primera máquina publicada en Hack The Box** y constituye un excelente punto de partida para nuevos entusiastas del pentesting.

Este repositorio documenta, paso a paso, el proceso de explotación guiado en modo *Guided Mode* de HTB, con enfoque didáctico y profesional, a cargo de r4ms4nt.

---

## 🧭 Objetivos del proyecto
- Desarrollar una metodología práctica de hacking ético.
- Aplicar técnicas reales de reconocimiento, enumeración y explotación.
- Practicar documentación profesional para entornos de certificación (OSCP, eJPT...).

---

## 📁 Estructura del repositorio

```
.
├── capturas
│   ├── Flag_1.png
│   ├── Flag_1submit.png
│   ├── Flag_2.png
│   ├── Flag_2submit.png
│   ├── grep_nmap.png
│   ├── logo_r4ms4nt_circular.png
│   ├── msfconsole1.png
│   ├── msfconsole2.png
│   ├── msfconsole_para_flag1_2.png
│   ├── msfconsole_para_flag1.png
│   ├── nmap_port_21.png
│   ├── nmap_smb.png
│   ├── nmap_top1000.png
│   ├── Task_10.png
│   ├── Task_11_Final.png
│   ├── Task_1.png
│   ├── Task_2.png
│   ├── Task_3.png
│   ├── Task_4.png
│   ├── Task_5.png
│   ├── Task_6.png
│   └── Task_9.png
├── .git
│   ├── branches
│   ├── COMMIT_EDITMSG
│   ├── config
│   ├── description
│   ├── HEAD
│   ├── hooks
│   │   ├── applypatch-msg.sample
│   │   ├── commit-msg.sample
│   │   ├── fsmonitor-watchman.sample
│   │   ├── post-update.sample
│   │   ├── pre-applypatch.sample
│   │   ├── pre-commit.sample
│   │   ├── pre-merge-commit.sample
│   │   ├── prepare-commit-msg.sample
│   │   ├── pre-push.sample
│   │   ├── pre-rebase.sample
│   │   ├── pre-receive.sample
│   │   ├── push-to-checkout.sample
│   │   └── update.sample
│   ├── index
│   ├── info
│   │   └── exclude
│   ├── logs
│   │   ├── HEAD
│   │   └── refs
│   ├── objects
│   │   ├── 04
│   │   ├── 07
│   │   ├── 09
│   │   ├── 10
│   │   ├── 18
│   │   ├── 1c
│   │   ├── 28
│   │   ├── 30
│   │   ├── 33
│   │   ├── 3d
│   │   ├── 3f
│   │   ├── 4b
│   │   ├── 4d
│   │   ├── 4f
│   │   ├── 54
│   │   ├── 56
│   │   ├── 5d
│   │   ├── 60
│   │   ├── 61
│   │   ├── 64
│   │   ├── 70
│   │   ├── 72
│   │   ├── 77
│   │   ├── 78
│   │   ├── 7c
│   │   ├── 82
│   │   ├── 85
│   │   ├── 8a
│   │   ├── 93
│   │   ├── 9e
│   │   ├── a1
│   │   ├── a6
│   │   ├── b1
│   │   ├── b6
│   │   ├── bd
│   │   ├── be
│   │   ├── cf
│   │   ├── dc
│   │   ├── de
│   │   ├── f2
│   │   ├── fb
│   │   ├── info
│   │   └── pack
│   └── refs
│       ├── heads
│       ├── remotes
│       └── tags
├── gitignore
├── lame_htb_manual.md
├── LICENSE
├── nmap
│   ├── ftp_version.gnmap
│   ├── ftp_version.nmap
│   ├── ftp_version.xml
│   ├── smb_version.gnmap
│   ├── smb_version.nmap
│   ├── smb_version.xml
│   ├── top1000_tcp.gnmap
│   ├── top1000_tcp.nmap
│   └── top1000_tcp.xml
├── README.md
└── tree_lame.txt

57 directories, 56 files
```

---

## 🧰 Herramientas utilizadas
- `nmap`, `netstat`, `ss` para escaneo de red
- `msfconsole` (Metasploit) para explotación
- `nc` para escuchar conexiones
- `Markdown` para documentación clara y replicable

---

## 🚩 Flags capturadas
- **Usuario:** `60fc5d64febbdebfe8cc331838bff0b0`
- **Root:** `c80b43503b56dc7b0dc82643157b4329`

---

## 📖 Manual completo
Puedes consultar el manual en [lame_htb_manual.md](./lame_htb_manual.md)

---

## ⚠️ Disclaimer
Este repositorio tiene fines estrictamente educativos. No está permitido aplicar estas técnicas sin autorización explícita sobre los sistemas objetivo.
