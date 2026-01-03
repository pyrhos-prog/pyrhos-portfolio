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
nmap -p- --open --min-rate 5000 -vvv -sS -Pn -n -vvv <10.10.11.80>

```

```bash
nmap -p- --open --min-rate 5000 