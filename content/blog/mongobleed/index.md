---
title: "MongoBleed: Exposición y abuso de instancias MongoDB sin autenticación"
date: 2026-01-03
draft: false
tags: ["mongodb", "databases", "misconfiguration", "pentesting", "infosec"]
categories: ["Seguridad", "Vulnerabilidades"]
---

## Introducción

**MongoBleed** es un término utilizado en la comunidad de seguridad para describir la **exposición masiva de bases de datos MongoDB sin autenticación**, accesibles directamente desde Internet.  
No se trata de una vulnerabilidad de software, sino de una **mala configuración crítica** que ha provocado filtraciones de datos, borrados masivos y campañas de extorsión.

---

## Contexto técnico

MongoDB, en versiones antiguas y en instalaciones mal configuradas, permitía:
- Escuchar en `0.0.0.0`
- Acceso sin credenciales
- Sin cifrado en tránsito
- Sin controles de red

Esto expone el servicio en el puerto por defecto:

