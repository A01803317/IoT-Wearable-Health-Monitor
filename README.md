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

## Integrantes

- Julian Cruz Valdez A01803317
- Abraham Alexander Velasco Gallo A01749765
