---
title: "HTB - Editor"
date: 2026-01-03
draft: false
tags: ["hackthebox", "ctf", "pentesting"]
categories: ["Writeups"]
difficulty: "Easy | Medium | Hard"
os: "Linux | Windows"
platform: "Hack The Box"
---

## Información general

- **Máquina:** Editor  
- **Plataforma:** Hack The Box  
- **Sistema operativo:** Linux / Windows  
- **Dificultad:** Easy  
- **Tipo:** CTF
- **Estado:** Retirada 

---

## Enumeración

### Escaneo de red

```bash
❯ sudo nmap -p- --open --min-rate 5000 -vvv -sS -n -Pn 10.10.11.80 -oN allports.txt
[sudo] contraseña para pyrhos: 
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times may be slower.
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-03 18:02 +0100
Initiating SYN Stealth Scan at 18:02
Scanning 10.10.11.80 [65535 ports]
Discovered open port 8080/tcp on 10.10.11.80
Discovered open port 22/tcp on 10.10.11.80
Discovered open port 80/tcp on 10.10.11.80
Completed SYN Stealth Scan at 18:02, 15.15s elapsed (65535 total ports)
Nmap scan report for 10.10.11.80
Host is up, received user-set (0.13s latency).
Scanned at 2026-01-03 18:02:23 CET for 15s
Not shown: 65532 closed tcp ports (reset)
PORT     STATE SERVICE    REASON
22/tcp   open  ssh        syn-ack ttl 63
80/tcp   open  http       syn-ack ttl 63
8080/tcp open  http-proxy syn-ack ttl 63

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 15.22 seconds
           Raw packets sent: 74143 (3.262MB) | Rcvd: 74136 (2.965MB)

```
El escaneo nos muestra 3 puertos abierto:
- El puerto 22 con un **ssh**
- El puerto 80 con un una web **http**
- El puerto 80080 con un proxy **http**

Ahora vamos a escanear los puertos abiertos en busca de mas información.

```bash
❯ sudo nmap -p22,80,8080 -sCV 10.10.11.80 -oN portscan.txt
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-03 18:08 +0100
Nmap scan report for 10.10.11.80
Host is up (0.14s latency).

PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 3e:ea:45:4b:c5:d1:6d:6f:e2:d4:d1:3b:0a:3d:a9:4f (ECDSA)
|_  256 64:cc:75:de:4a:e6:a5:b4:73:eb:3f:1b:cf:b4:e3:94 (ED25519)
80/tcp   open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://editor.htb/
8080/tcp open  http    Jetty 10.0.20
| http-webdav-scan: 
|   WebDAV type: Unknown
|   Server Type: Jetty(10.0.20)
|_  Allowed Methods: OPTIONS, GET, HEAD, PROPFIND, LOCK, UNLOCK
| http-robots.txt: 50 disallowed entries (15 shown)
| /xwiki/bin/viewattachrev/ /xwiki/bin/viewrev/ 
| /xwiki/bin/pdf/ /xwiki/bin/edit/ /xwiki/bin/create/ 
| /xwiki/bin/inline/ /xwiki/bin/preview/ /xwiki/bin/save/ 
| /xwiki/bin/saveandcontinue/ /xwiki/bin/rollback/ /xwiki/bin/deleteversions/ 
| /xwiki/bin/cancel/ /xwiki/bin/delete/ /xwiki/bin/deletespace/ 
|_/xwiki/bin/undelete/
|_http-open-proxy: Proxy might be redirecting requests
| http-cookie-flags: 
|   /: 
|     JSESSIONID: 
|_      httponly flag not set
| http-title: XWiki - Main - Intro
|_Requested resource was http://10.10.11.80:8080/xwiki/bin/view/Main/
|_http-server-header: Jetty(10.0.20)
| http-methods: 
|_  Potentially risky methods: PROPFIND LOCK UNLOCK
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.55 seconds
```

Con este segundo escaneo vemos mas información sobre cada puerto abierto
- En el puerto 22 hay un **OpenSSH 8.9p1** corriendo en un **Ubuntu 3ubuntu0.13**
- En la web del puerto 80 vemos una redirección al dominio **editor.htb**
- En el puerto 8080 Esta corriendo un servidor **Jetty 10.0.20**, además de que nos muestra el **robots.txt**:
```javascript
| /wiki/bin/viewattachrev/ 
| /xwiki/bin/viewrev/ 
| /xwiki/bin/pdf/ 
| /xwiki/bin/edit/ 
| /xwiki/bin/create/ 
| /xwiki/bin/inline/ 
| /xwiki/bin/preview/ 
| /xwiki/bin/save/ 
| /xwiki/bin/saveandcontinue/ 
| /xwiki/bin/rollback/ 
| /xwiki/bin/deleteversions/ 
| /xwiki/bin/cancel/ 
| /xwiki/bin/delete/
| /xwiki/bin/deletespace/ 
|_/xwiki/bin/undelete/
```
### /etc/hosts
Ahora vamos añadir el dominio encontrado anteriormente al /etc/hosts para que el sistema traduzca la IP de la maquina a ese dominio.

```bash
echo "10.10.11.80   editor.htb" >> /etc/hosts
```  
Así podremos entrar a la web a traves del dominio.

### Puerto 80 - Servicio web

Al entrar a la página web a traves del puerto 80 vemos lo siguiente:

![](/content/htb/maquina-editor/imgs/web.png)

Una web de un editor de código compatible con linux y windows, sin nada interesante en la pagina a parte de los dos enlaces de descarga del programa y el apartado Docs, que nos redirige a wiki.editor.htb.

### Puerto 8080 - Servicio web

Al entrar al subdominio wiki.editor.htb vemos la wiki del editor que habiamos visto anteriormente y que esta hecha con XWiki.

![](/content/htb/maquina-editor/imgs/puerto-8080.png)

Además tambien vemos 2 cosas muy importantes:
- Un usuario: "Neal Bagwell"
- Una versión: "XWiki Debian 15.10.8"
### XWiki

Lo primero que debemos hacer no es buscar una vulnerabilidad si no entender las tecnologías que utiliza la página para despúes buscar la vulnerabilidad de manera efectiva.

#### ¿Que es XWiki?

>XWiki es una plataforma de software wiki de código abierto escrita en Java, diseñada para facilitar la colaboración y el manejo del conocimiento dentro de organizaciones.

XWiki proporciona funciones clave que permiten una edición colaborativa fácil y segura:

- Editor WYSIWYG avanzado, incluidos editores de enlaces y macros;
- Adjuntar y previsualizar imágenes y archivos adjuntos de oficina;
- Menciones, me gusta y notificaciones de usuarios;
- Comentarea și annotare;
- Historial completo de cambios;
- Edición in situ.

Con esto ya sabemos mejor lo que estamos viendo.

#### Versión de XWiki

Si buscamos la version de XWiki que utiliza la web podemos ver que hay una vulnerabilidad que permite ejecucion remota de comandos "CVE-2025-24893".

[PoC CVE-2025-24893 Rev Shell](https://github.com/AzureADTrent/CVE-2025-24893-Reverse-Shell)



