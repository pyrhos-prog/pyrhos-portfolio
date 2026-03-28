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

- Direccion: OxB0C5FC58010D79eAFAD34854F4346dBD8068D0E1

!()[imgs-atencion-extorsion/etherscan.png]

Al introducir la wallet en etherscan podemos ver las transacciones que se han hecho a través de ella
