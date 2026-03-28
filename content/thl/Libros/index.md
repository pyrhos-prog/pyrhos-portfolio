---
title: "Libros - The Hackers Labs"
date: 2026-03-28
draft: false
tags: ["ctf", "OSINT", "writeup"]
categories: ["Writeups"]
difficulty: "Avanzado"
os: "n/p"
platform: "The Hackers Labs"
---


## Información general

* **Máquina:** Libros
* **Plataforma:** The Hackers Labs
* **Dificultad:** Principiante
* **Tipo:** OSINT

---

## Descripción del Desafio

### Extorsión

> Nuestro representante se ha perdido.
La última vez visto fue en abril de 2024, dirigiéndose a comprar un libro en Gran Vía (Madrid), cerca del Primark.

>En ese momento, se encontraba cerrando un trato sobre una nueva exposición de TheHackersLabs.
Algo se debió torcer... Íbamos hablando por teléfono cuando, a pocos metros, me dijo:

>“No puede ser… ya lo han cerrado, el trato está hecho y el cartel del evento está anunciado con la fecha… y encima con un logo similar al de la explosión.”


### Información relevante:
> hay información importante en esta descripción


**Último lugar visto:** Gran via, cerca del Primark

**Fecha:** Abril de 2024

**Contexto de la llamada:** A pocos metros de la tienda de libros el representante dice que el trato ya a sido cerrado, esta anunciado con la fecha y tiene un logo similar al de la exposición.



### Preguntas a resolver

1. ¿Con quién se reunió?
2. ¿Cuál es su teléfono?



## Procedimiento

### Tienda de libros


Vamos a empezar buscando tiendas de libros en Gran Vía para saber donde fue el último lugar al que entró y poder seguir la pista.

![](imgs-libros/tienda-libros.png)

- la casa del libro es la opción mas probable.

Ahora vamos a buscar en google maps la casa del libro en abril de 2024 para buscar información relevante.

![](imgs-libros/cartel.png)

Indagando un poco, encontramos un cartel de una exposición el Dia 28 de abril de 2024 y encima de ella un logo de un tomate.

Ahora vamos a buscar información sobre The Hackers Labs

![](imgs-libros/web.png)

Dentro de la web al investigarla encontramos un logo de un tomate 

![](imgs-libros/logo.png)

Ahora vamos a buscar en los metadatos de la imagen información interesante.

``` bash
pyrhos@fedora:~$ exiftool microchoft1.png 
ExifTool Version Number         : 13.10
File Name                       : microchoft1.png
Directory                       : .
File Size                       : 463 kB
File Modification Date/Time     : 2025:09:17 12:29:57+02:00
File Access Date/Time           : 2026:03:28 17:16:13+01:00
File Inode Change Date/Time     : 2026:03:28 17:16:13+01:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1024
Image Height                    : 1024
Bit Depth                       : 8
Color Type                      : Palette
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Palette                         : (Binary data 768 bytes, use -b option to extract)
Comment                         : Aurelio Bravo
Image Size                      : 1024x1024
Megapixels                      : 1.0

```
Encontramos un nombre, Aurelio Bravo.

Buscando en el instagram de The Hackers Labs las publicaciones de la fecha de la exposicion encontramos una publicacion.

![](imgs-libros/social.png)

En ella vemos algo que parece ser base64.

```bash
pyrhos@fedora:~$ echo "MzI1IDU5NCA5NTI=" | base64 -d

325 594 952
```
Al pasar la cadena a texto nos devuelve algo que parece ser un número.


Con esto ya tendriamos lo necesario para resolvera las preguntas del reto:

**1. ¿Con quién se reunió?** Aurelio Bravo

**2. ¿Cuál es su teléfono?** 
325 594 952
