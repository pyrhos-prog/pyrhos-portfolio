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

- **Máquina:** NombreMaquina  
- **Plataforma:** Hack The Box  
- **Sistema operativo:** Linux / Windows  
- **Dificultad:** Easy / Medium / Hard  
- **Tipo:** CTF / Realista  
- **Estado:** Retirada / Activa  

---

## Enumeración

### Escaneo de red

```bash
nmap -p- --open -sS -Pn -n -vvv <IP>
