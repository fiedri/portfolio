---
title: 'Cómo apagué la música de una fiesta para poder dormir'
description: 'Cuando el respeto al descanso falla, el conocimiento técnico entra en acción. En este artículo detallo cómo utilicé herramientas de auditoría de red (Nmap, arpspoof y hping3) para escalar un ataque de denegación de servicio y silenciar un equipo de sonido que no permitía dormir.'
date: '12/20/2025'
tags: ['Linux', 'Hacking', 'Networking']
published: true
---
Creo que una de las cosas que más me causó indignación este año fue que haya parranda en mi refugio temporal (la casa donde vivo), no estar invitado y tener que calarme la música y la gente cantando karaoke hasta tarde. Todo esto sacrificando mis valiosas horas de sueño por pura obstinación ajena.

Hasta que recordé que soy informático. Me pregunté qué podía hacer con este vasto conocimiento en las artes digitales y recordé que hace tiempo había probado un script para realizar **Bluesmack** (un ataque de denegación de servicio a dispositivos Bluetooth). Mi primera idea fue imponer mi poder como hacker silenciando el receptor directamente. Sin embargo, encontrar la dirección MAC del radio fue imposible; tras tres horas de búsqueda fallida, escuché un anuncio de YouTube saliendo por las cornetas.

Eso lo cambió todo. Significaba que no dependían solo del Bluetooth, sino que usaban el Wi-Fi para su música mundana. En ese momento entendí que mi objetivo de dormir aún no estaba perdido.

---

## Paso 1: Localización y Reconocimiento de Red

Para atacar, primero necesitaba un mapa de mi red local. El primer paso fue identificar la **IP del Router**. Utilicé el comando:

`ip route show`

Este comando devuelve la tabla de enrutamiento del sistema. La línea que nos interesa es la que comienza con `default via`, que indica la dirección del nodo central:

> **Ejemplo de salida:**
> `default via 192.168.0.1 dev wlx88947e9b4dab proto dhcp metric 600`
> *Aquí confirmamos que el router es la IP **192.168.0.1**.*

Con la dirección del router clara, utilicé **Nmap** para realizar un escaneo de dispositivos activos en el segmento de red (`/24` que abarca de la IP .1 a la .254):

`sudo nmap -sn 192.168.0.0/24`

El parámetro `-sn` indica un "Ping Scan", que detecta dispositivos encendidos sin realizar un escaneo de puertos profundo, lo que lo hace mucho más rápido.

---

## Intento 1: Inundación por ICMP (Ping Flood)

Con la lista de sospechosos en mano (excluyendo mi PC y el router), identifiqué los teléfonos que estaban haciendo el streaming. Mi primer movimiento fue un **Ping Flood**.

`sudo ping -f <ip_del_dispositivo>`

El parámetro `-f` (flood) envía paquetes ICMP tan rápido como el sistema puede procesarlos o tan pronto como regresan. Ejecuté esto en varias terminales simultáneamente contra distintas IPs sospechosas. Aunque la música presentaba interrupciones, el streaming lograba recuperarse debido a que los routers modernos tienen mecanismos para priorizar o limitar este tipo de tráfico básico.

---

## Intento 2: Ataque Man-In-The-Middle (ARP Spoofing)

Decidí escalar el ataque mediante una técnica de **Envenenamiento de Tablas ARP**. El objetivo era engañar al router para que pensara que mi PC era el teléfono, y al teléfono para que pensara que mi PC era el router.

Utilicé la herramienta **arpspoof** en dos terminales:

1. `sudo arpspoof -i interfaz -t 192.168.0.109 192.168.0.1` (Engañando al teléfono).
2. `sudo arpspoof -i interfaz -t 192.168.0.1 192.168.0.109` (Engañando al router).

Al interceptar el tráfico, simplemente desactivé el reenvío de paquetes en mi kernel (`ip_forward=0`), convirtiendo mi laptop en un "agujero negro" para sus datos. Sin embargo, mi tarjeta de red inalámbrica no soportó el volumen de paquetes y el ataque no fue persistente.

---

## Intento 3: Saturación de Capa 4 (TCP SYN Flood), la tercera es la vencida.

Al ver que los métodos anteriores fallaban, utilicé uno mas rudo: **hping3**. A diferencia del ping común (Capa 3), este ataque se enfoca en la Capa de Transporte (Capa 4), específicamente en el protocolo **TCP**.

`sudo hping3 -S -p 80 --flood 192.168.0.120`

### ¿Por qué funcionó este método?

1. **Modo Flood:** Envía paquetes a la máxima velocidad posible sin esperar respuesta, saturando el ancho de banda.
2. **Flag SYN (`-S`):** Envía peticiones de inicio de conexión. El dispositivo de la fiesta se ve obligado a reservar memoria para cada conexión falsa que yo inicio. Al recibir millones de estas peticiones, el procesador del teléfono colapsa intentando gestionarlas todas.
3. **Puerto 80:** Al atacar el puerto estándar de navegación web, el dispositivo no puede ignorar el tráfico fácilmente.

El resultado fue inmediato: el teléfono de los invitados se quedó sin recursos para mantener el buffer de YouTube. La música se cortó definitivamente y, ante la frustración de no tener conexión, finalmente apagaron el radio. La victoria fue total.
