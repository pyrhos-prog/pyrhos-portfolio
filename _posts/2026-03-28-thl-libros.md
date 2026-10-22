---
layout: post
title: "Libros — The Hackers Labs"
date: 2026-03-28 17:00:00 +0200
categories: ["Writeups", "OSINT"]
tags: ["ctf", "osint", "writeup", "thehackerslabs"]
platform: "The Hackers Labs"
difficulty: "Easy"
description: "Resolución del reto OSINT 'Libros' de The Hackers Labs: análisis de metadatos con ExifTool, geolocalización en Gran Vía e investigación en fuentes abiertas."
toc: true
status: "Resuelta"
accent: "94 180 248"
---

## Información general

* **Reto:** Libros
* **Plataforma:** The Hackers Labs
* **Dificultad:** Principiante / Intermedio
* **Tipo:** OSINT

---

## Descripción del Desafío

> Nuestro representante se ha perdido. La última vez visto fue en abril de 2024, dirigiéndose a comprar un libro en Gran Vía (Madrid), cerca del Primark.
> En ese momento, se encontraba cerrando un trato sobre una nueva exposición de TheHackersLabs. Algo se debió torcer... Íbamos hablando por teléfono cuando, a pocos metros, me dijo:
> *"No puede ser… ya lo han cerrado, el trato está hecho y el cartel del evento está anunciado con la fecha… y encima con un logo similar al de la exposición."*

### Datos clave:
* **Último lugar visto:** Gran Vía (Madrid), en las inmediaciones del Primark.
* **Fecha:** Abril de 2024.
* **Contexto:** Tienda de libros cercana, cartel de exposición cerrado con un logo de tomate.

### Preguntas a resolver:
1. ¿Con quién se reunió?
2. ¿Cuál es su teléfono?

---

## Procedimiento

### 1. Búsqueda y geolocalización

Buscamos tiendas de libros en Gran Vía próximas al Primark:

![Tienda de Libros](/assets/imgs-libros/tienda-libros.png)

La opción más evidente es **La Casa del Libro**. Utilizando Google Street View con fecha de abril de 2024 encontramos el cartel de la exposición anunciado para el día 28 de abril de 2024 con el logo de un tomate:

![Cartel](/assets/imgs-libros/cartel.png)

### 2. Investigación web y metadatos

Examinando la web de The Hackers Labs encontramos la referencia gráfica del evento:

![Web](/assets/imgs-libros/web.png)
![Exposición](/assets/imgs-libros/exposicion.png)

Descargamos la imagen e inspeccionamos sus metadatos con **ExifTool**:

```bash
❯ exiftool microchoft1.png 
File Name                       : microchoft1.png
File Size                       : 463 kB
Comment                         : Aurelio Bravo
Image Size                      : 1024x1024
```

Obtenemos el nombre: **Aurelio Bravo**.

### 3. Redes sociales y decodificación

Revisando las publicaciones de The Hackers Labs en Instagram en las fechas del evento localizamos un post con una cadena sospechosa en base64:

![Social](/assets/imgs-libros/social.png)

Decodificamos desde la terminal:

```bash
❯ echo "MzI1IDU5NCA5NTI=" | base64 -d
325 594 952
```

---

## Respuestas del Desafío

1. **¿Con quién se reunió?**: `Aurelio Bravo`
2. **¿Cuál es su teléfono?**: `325 594 952`
