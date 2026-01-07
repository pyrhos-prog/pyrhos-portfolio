---
title: "CTF - Nombre de la máquina"
date: 2026-01-05
draft: false
tags: ["ctf", "pentesting"]
categories: ["Writeups"]
difficulty: "Easy | Medium | Hard"
os: "Linux | Windows"
platform: "Hack The Box | TryHackMe | VulnHub"
---


## Información general

* **Máquina:** [Nombre]
* **Plataforma:** [Hack The Box / TryHackMe / etc.]
* **Sistema operativo:** [OS]
* **Dificultad:** [Dificultad]
* **Tipo:** CTF
* **Estado:** [Activa / Retirada]

---

## Enumeración

### Escaneo de red

```bash
# Comando de nmap para descubrimiento de puertos
❯ sudo nmap -p- --open --min-rate 5000 -vvv -sS -n -Pn 10.10.11.97 -oN allports.txt
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times may be slower.
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-04 20:01 +0100
Initiating SYN Stealth Scan at 20:01
Scanning 10.10.11.97 [65535 ports]
Discovered open port 22/tcp on 10.10.11.97
Discovered open port 80/tcp on 10.10.11.97
Completed SYN Stealth Scan at 20:02, 15.19s elapsed (65535 total ports)
Nmap scan report for 10.10.11.97
Host is up, received user-set (0.21s latency).
Scanned at 2026-01-04 20:01:51 CET for 15s
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE REASON
22/tcp open  ssh     syn-ack ttl 63
80/tcp open  http    syn-ack ttl 63

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 15.28 seconds
           Raw packets sent: 73785 (3.247MB) | Rcvd: 73617 (2.945MB)

```

[Descripción de los puertos encontrados y servicios detectados]

```bash
# Escaneo detallado de servicios y scripts
❯ sudo nmap -p22,80 -sCV 10.10.11.97 -oN portscan.txt
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-04 20:03 +0100
Nmap scan report for 10.10.11.97
Host is up (0.11s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 1f:de:9d:84:bf:a1:64:be:1f:36:4f:ac:3c:52:15:92 (ECDSA)
|_  256 70:a5:1a:53:df:d1:d0:73:3e:9d:90:ad:c1:aa:b4:19 (ED25519)
80/tcp open  http    Apache httpd 2.4.52
|_http-title: Did not follow redirect to http://gavel.htb/
|_http-server-header: Apache/2.4.52 (Ubuntu)
Service Info: Host: gavel.htb; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.24 seconds
```

### /etc/hosts

Añadimos el dominio encontrado al **/etc/hosts**

```bash
echo "10.10.11.97    gavel.htb" >> /etc/hosts
```

### Puerto 80 - HTTP
Al entrar a la web vemos una pagina de una casa de subastas. En la página se comenta que esta es la version 2.0 porque la 1.0 " Terminó en fuego, demandas y una luna misteriosamente desaparecida."
![](imgs-gavel/web.png)
---

## Explotación

### [Nombre de la Vulnerabilidad / CVE]

[Explicación teórica de la vulnerabilidad encontrada]

#### PoC (Proof of Concept)

{{< github repo="[USER]/[REPO]" showThumbnail=true >}}

[Instrucciones de uso del script o pasos para la explotación manual]

```bash
# Ejemplo de ejecución
python3 exploit.py -u http://[dominio.htb] -c "whoami"
```

[Captura o texto de la shell obtenida]

---

## Escalada de privilegios

### Enumeración del sistema

[Análisis de vectores de escalada: SUID, procesos, archivos de configuración, capacidades, etc.]

```bash
# Ejemplo: Búsqueda de binarios SUID
find / -perm -4000 2>/dev/null
```

### Usuario: [Nombre]

[Pasos específicos para pivotar a otro usuario o explotar una mala configuración local]

#### Flag de Usuario

```bash
user@maquina:~$ cat user.txt
```

### Root (Privesc)

[Análisis del vector final para alcanzar privilegios de administrador]

```bash
# Comandos finales de escalada
sudo -l
# o ejecución de exploit local
```

#### Flag de Root

```bash
root@maquina:~# cat /root/root.txt
```
