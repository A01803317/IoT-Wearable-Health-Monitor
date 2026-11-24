# IoT Wearable Health Monitor

## Descripción

Sistema wearable basado en Internet de las Cosas (IoT) para monitorear en tiempo real variables biomédicas y de movimiento del usuario.

Actualmente, el proyecto se encuentra en la Etapa 1, enfocada en el diseño de la arquitectura, selección de sensores y tecnologías.

## Objetivo

Desarrollar un dispositivo wearable capaz de recopilar, transmitir, almacenar y visualizar variables biomédicas y de movimiento del usuario.

## Variables monitoreadas

- Frecuencia cardíaca (BPM)
- Saturación de oxígeno (SpO₂)
- Temperatura
- Aceleración y movimiento
- Orientación

## Hardware

- **ESP32:** Microcontrolador principal con conectividad Wi-Fi.
- **MAX30102:** Frecuencia cardíaca y SpO₂.
- **MLX90614:** Temperatura.
- **MPU6050:** Acelerómetro y giroscopio para medir movimiento y orientación.

## Arquitectura IoT

### 1. Percepción
Los sensores recopilan las variables biomédicas y de movimiento del usuario.

### 2. Red
El ESP32 transmite los datos por Wi‑Fi mediante MQTT.

### 3. Procesamiento
Un broker MQTT recibe los datos. Se propone utilizar XAMPP, PHP y MySQL para el procesamiento y almacenamiento.

### 4. Aplicación
Un dashboard web permitirá visualizar las mediciones e historial del usuario.

### 5. Negocio
Los datos podrán utilizarse para consultar tendencias y generar alertas sobre las mediciones.

## Flujo del sistema

Sensores → ESP32 → Wi-Fi/MQTT → Broker MQTT → Base de datos → Dashboard

## Estado actual

El proyecto se encuentra en fase de diseño y selección de componentes. Las siguientes etapas incluyen la integración de sensores, la programación del ESP32, el almacenamiento de datos y el desarrollo del dashboard. 
Actualización: Etapa (02/11/26) 
Se hizo:
1.-Montaje físico y pruebas de lectura
2.-Análisis de señal
3.-Conexion a Wi-fi
4.-Justificación de Wi-fi
5.-Preguntas de reflexión

## Integrantes

- Julian Cruz Valdez A01803317
- Abraham Alexander Velasco Gallo A01749765

## Etapa 2:

1.Montaje físico y pruebas de lectura: Se conectaron los sensores al ESP32 en la protoboard. Se programó un sketch que lee los valores y los imprime en el monitor serial.

2.Análisis de señal:Se observó que el sensor MAX30102 presenta "ruido" debido al movimiento del dedo, la presión ejercida o la luz externa. Se concluyó que se necesita una posición estable de dedo para lecturas confiables.

3.Conexión a Wi-fi: Se configuró el ESP32 para conectarse a una red local. Se obtuvo una dirección IP y se validó la conexión mediante una petición HTTP exitosa.

4.Justificación de Wi-fi: Se argumentó que se elige Wi-fi sobre Bluetooth porque permite una conexión directa a la red local y facilita el envío de datos a un servidor(broker) mediante protocolos como HTTP o MQTT, ideal para integrarse con bases de datos web.

5.Preguntas de reflexión: Se respondieron preguntas clave sobre por qué el MAX30102 requiere de dos longitudes de onda(roja e infrarrojo) para medir el SpO2, y se propusieron actuadores alternativos para personas con discapacidad(guantes con vibración, luces estroboscópicas o pulsaciones eléctricas suaves).

## Etapa 3:
La Etapa 3 se enfocó en la estructuración de datos y la comunicación del dispositivo utilizando un microcontrolador ESP32 junto con los sensores MLX90614(temperatura), MAX30102(oximetría/pulso), MPU6050(aceleración).

## 1.Diseño y documentación del esquema de datos (Parte 1):

a)Definición de variables: Se creó una tabla formal documentando 10 variables clave para el monitoreo del adulto mayor. Se especificó el nombre de cada campo (ej.: temp_amb_c), su unidad de medida, el tipo de dato y su rango esperado.

b)Payload JSON: Se estableció el uso de un formato JSON plano para organizar las lecturas, facilitando su envío y lectura. Se documentó el uso de la librería "ArduinoJson" en el ESP32 para armar este paquete de datos.

c)Análisis y reflexión: Se respondieron las preguntas críticas de la etapa, concluyendo que es vital incluir unidades en los nombres de los campos (ej.: _c) para evitar errores de interpretación; el formato JSon permite agregar nuevos sensores fácilmente sin romper el sistema; y el uso de estándares como IPSO facilita la interoperabilidad("plug and play") entre diferentes plataformas. 

## 2.Publicación y comunicación MQTT (Parte 2):

a)Conexión y envío: Se configuró la conexión al broker compartido para publicar los datos periódicamente en el tópico del equipo ( reto2026/eq01/data).

b)Calidad de Servicio (QoS): Se seleccionó el "QoS 1" para garantizar que los datos médicos lleguen al servidor al menos una vez, evitando pérdidas de información vital.

c)Análisis y reflexión: Se justificó el uso de MQTT sobre HTTP por su bajo consumo de batería y ancho de banda (ideal para wearable). Además, se analizaron los riesgos de publicar en tópicos erróneos (colisión de datos) y la importancia crítica del mecanismo LWT para alertar al dashboard si el dispositivo se apaga, pierde conexión WI_FI o sufre un impacto (posible caída del paciente).

## 3.Documentación y entregables:
Se recopiló toda la información técnica, el diseño del esquema y las reflexiones para ser subidos al repositorio de "Github" del equipo, cumpliendo con los entregables solicitados.

## Etapa 3 – Integración y comunicación del sistema VitaSense

Durante la tercera etapa del proyecto VitaSense se realizaron avances en la integración del hardware, la comunicación por internet y el almacenamiento de información.

### Avances realizados

- Integración del ESP32 con los sensores MAX30102, MLX90614 y MPU6050.
- Visualización de las mediciones en una pantalla OLED.
- Configuración de la comunicación mediante el protocolo MQTT.
- Publicación de datos en formato JSON al broker MQTT.
- Implementación de un programa en Python para recibir y almacenar mediciones en MySQL.
- Actualización y normalización de la base de datos hasta la tercera forma normal (3FN).
- Implementación de un sistema de detección de impactos y de generación de alertas.
- Desarrollo de la interfaz web para la visualización de las mediciones.
- Consideración de criterios de usabilidad y sostenibilidad.

### Estado actual

El prototipo cuenta con comunicación MQTT y se han realizado pruebas exitosas de almacenamiento de mediciones en la base de datos. Actualmente se trabaja en la integración final de la interfaz web y en la validación completa del sistema.
