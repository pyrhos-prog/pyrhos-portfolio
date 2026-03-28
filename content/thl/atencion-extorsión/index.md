---
title: "¡Atención Extorsion! - The Hackers Labs"
date: 2026-03-28
draft: false
tags: ["ctf", "OSINT", "writeup"]
categories: ["Writeups"]
difficulty: "Avanzado"
os: "n/p"
platform: "The Hackers Labs"
---


## Información general

* **Máquina:** ¡Atención Extorsion!
* **Plataforma:** The Hackers Labs
* **Dificultad:** Avandazdo
* **Tipo:** OSINT

---

## Descripción del Desafio

### Extorsión

> Estimados miembros de las FFCCSE,
Me dirijo a ustedes con un asunto de extrema gravedad que requiere su atención inmediata. He sido objeto de extorsión, donde se me ha exigido transferir 300 ETH a una dirección desconocida. El extorsionador amenaza con hacer pública mi interés por aprender hacking en The Hackers Labs, lo que podría tener serias repercusiones para mi reputación y seguridad.
> A continuación, detallo los pasos que considero cruciales para abordar esta situación:
> - Identificación de la Transacción: Rastrear la transacción involucrada y recopilar información clave, incluyendo el valor transferido y las direcciones de envío y recepción.
> - Análisis de la Billetera Destinataria: Examinar la actividad de la billetera que ha recibido los fondos, buscando detectar posibles pagos o transacciones sospechosas que puedan estar relacionadas con el extorsionador.
>- Informe de Resultados: Elaborar un informe detallado sobre los hallazgos de la investigación, con el objetivo de identificar y exponer al extorsionador. Este informe será fundamental para realizar la denuncia correspondiente.

> En la captura de pantalla adjunta se encuentra la dirección de la billetera involucrada. Recomiendo que se copie esta información en un formato de texto, ya que es una captura de pantalla. Utilizar esta dirección será clave para resolver gran parte del problema. Agradezco de antemano su atención y apoyo en esta delicada situación.

![](imgs-atencion-extorsion/correo-extorsion.jpg)

### Información relevante:
> De este correo podemos sacar basante información.

**Nombre del grupo de extorsionadores:** los que saben todo

**Fecha:** 03-Oct-2024 2:30:47

**Cantidad transferida:** 300 Eth

**Tiempo para transferirla:** 24 horas

**Wallet:** 0xB0C5Fc58010D79eAFAD34854F4346dBD8068D0E1


### Preguntas a resolver

1. ¿Cuál fue la cantidad exacta transferida? 
2. ¿Cuál fue la dirección de envío?
3. ¿Cuál fue la dirección de recepción?
4. ¿Qué plataforma fue utilizada para la operación?
5. ¿En qué fecha y hora se realizó la operación?
6. ¿Cuál es el hash de la transacción?


## Procedimiento

### Dirección de la billetera

Vamos a empezar buscando información sobre la direccion de la billetera del correo.

- Direccion: 0xB0C5Fc58010D79eAFAD34854F4346dBD8068D0E1


Al introducir la wallet en etherscan podemos ver las transacciones que se han hecho a través de ella.

![](imgs-atencion-extorsion/etherscan.png)

Ahora vamos a filtrar las transacciones por la fecha del correo, que sean transacciones solo de entrada 

![](imgs-atencion-extorsion/filtro-etherscan.png)

Nos sale una transaccion de **300.9983** ETH, encaja perfectamente asi que vamos a ver los detalles. 

![](imgs-atencion-extorsion/detalles-transaccion.png)

En los detalles vemos que esta toda la información necesaria para resolver las pregunta del reto.

**1. ¿Cuál fue la cantidad exacta transferida?** 300.9983 ETH

**2. ¿Cuál fue la dirección de envío?** 
0x28c6c06298d514db089934071355e5743bf21d60

**3. ¿Cuál fue la dirección de recepción?** 0xB0C5Fc58010D79eAFAD34854F4346dBD8068D0E1

**4. ¿Qué plataforma fue utilizada para la operación?** Binance

**5. ¿En qué fecha y hora se realizó la operación?** Oct-03-2024 02:30:47 PM

**6. ¿Cuál es el hash de la transacción?** 0x00ae9dd1f5456f01c0b2458dcc88596a7dd081a2cdf2f581f702fa6333ba777a
