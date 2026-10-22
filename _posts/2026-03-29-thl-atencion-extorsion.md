---
layout: post
title: "¡Atención Extorsión! — The Hackers Labs"
date: 2026-03-29 18:00:00 +0200
categories: ["Writeups", "OSINT"]
tags: ["ctf", "osint", "blockchain", "etherscan", "thehackerslabs"]
platform: "The Hackers Labs"
difficulty: "Medium"
description: "Resolución del reto OSINT y Blockchain '¡Atención Extorsión!' de The Hackers Labs: rastreo de billeteras Ethereum, análisis en Etherscan y extracción de transacciones."
toc: true
status: "Resuelta"
accent: "255 175 0"
---

## Información general

* **Reto:** ¡Atención Extorsión!
* **Plataforma:** The Hackers Labs
* **Dificultad:** Intermedio
* **Tipo:** OSINT & Blockchain Forensics

---

## Descripción del Desafío

Un usuario reporta un correo de extorsión solicitando 300 ETH con amenazas de divulgación pública:

![Correo de Extorsión](/assets/imgs-atencion-extorsion/correo-extorsion.jpg)

### Datos extraídos:
* **Remitente:** "los que saben todo"
* **Fecha:** 03-Oct-2024 02:30:47 PM
* **Cantidad:** ~300 ETH
* **Dirección de Billetera:** `0xB0C5Fc58010D79eAFAD34854F4346dBD8068D0E1`

### Preguntas a resolver:
1. ¿Cuál fue la cantidad exacta transferida?
2. ¿Cuál fue la dirección de envío?
3. ¿Cuál fue la dirección de recepción?
4. ¿Qué plataforma fue utilizada para la operación?
5. ¿En qué fecha y hora se realizó la operación?
6. ¿Cuál es el hash de la transacción?

---

## Procedimiento

Consultamos la dirección en **Etherscan** (`https://etherscan.io`):

![Etherscan](/assets/imgs-atencion-extorsion/etherscan.png)

Filtramos las transacciones entrantes (In) por la fecha indicada en la comunicación:

![Filtro Etherscan](/assets/imgs-atencion-extorsion/filtro-etherscan.png)

Localizamos una transferencia exacta de **300.9983 ETH** y analizamos el detalle de la transacción:

![Detalles de Transacción](/assets/imgs-atencion-extorsion/detalles-transaccion.png)

---

## Respuestas del Desafío

1. **Cantidad exacta transferida:** `300.9983 ETH`
2. **Dirección de envío:** `0x28c6c06298d514db089934071355e5743bf21d60`
3. **Dirección de recepción:** `0xB0C5Fc58010D79eAFAD34854F4346dBD8068D0E1`
4. **Plataforma utilizada:** `Binance`
5. **Fecha y hora:** `Oct-03-2024 02:30:47 PM`
6. **Hash de la transacción:** `0x00ae9dd1f5456f01c0b2458dcc88596a7dd081a2cdf2f581f702fa6333ba777a`
