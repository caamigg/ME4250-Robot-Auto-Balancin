# WALL-E Balancer: Robot Auto-Balancín

### Proyecto semestral de Mecatrónica - ME4250

<p align="center">
  <img src="./Registros audiovisuales/foto_final_robot.jpg" width="300">
  
  <em>Figura 1: Prototipo final "Wall-E"</em>
</p>

## 📋 Resumen del proyecto

Este repositorio contiene la documentación técnica, diseño mecánico y firmware del **"Wall-E Balancer"**, un robot de dos ruedas coaxiales capaz de mantener el equilibrio vertical mediante un sistema de control de lazo cerrado.

El proyecto fue desarrollado como parte del curso **ME4250 Mecatrónica** en el Departamento de Ingeniería Mecánica de la **Universidad de Chile**, durante el semestre Primavera 2025. El objetivo principal fue integrar diseño mecánico, electrónica y teoría de control para estabilizar un péndulo invertido sobre ruedas.

---

## Equipo de trabajo

**Curso:** ME4250 Mecatrónica  
**Institución:** Facultad de Ciencias Físicas y Matemáticas, Universidad de Chile  
**Semestre:** Primavera 2025  

**Integrantes:**
* **Camila Aravena**
* **Carlos Aravena**
* **Jan Fergusson**
* **Marcelo Guaquel**
* **Antonella Savoy**

**Cuerpo docente:**
* *Profesor:* Harold Valenzuela
* *Auxiliares:* Francisco Cáceres, Fernando Navarrete

---

## Evolución del diseño e iteración

Nuestro diseño pasó por una etapa crítica de iteración para asegurar la estabilidad mecánica:

1.  **Concepto inicial (Mono-Ciclista):** Originalmente se planteó un diseño basado en un personaje sobre un monociclo. Sin embargo, las pruebas preliminares mostraron problemas de sujeción de la estética superior durante el movimiento del carro.
2.  **Diseño final (Estética Wall-E):** Se pivotó hacia una estructura rígida inspirada en "Wall-E". Esta modificación permitió:
    * Fijar firmemente los componentes superiores.
    * Elevar el Centro de Masa (CoM) de manera controlada para mejorar la inercia rotacional según los requerimientos.
    * Alojar la electrónica de forma más ordenada y segura.

| Concepto inicial | Diseño final implementado |
|:---:|:---:|
| <img src="./Registros audiovisuales/Estetica inicial.jpg" width="300"> | <img src="./Registros_audiovisuales/diseño_walle.jpg" width="300"> |
| *Problemas de sujeción mecánica* | *Estructura rígida y optimizada* |

---

## Decisiones de diseño y selección de componentes

Para cumplir con los requerimientos físicos del sistema, se realizaron las siguientes selecciones técnicas:

### 1. Selección de motores (torque y peso)
Se seleccionaron **2 motores DC con caja reductora** (tipo estándar "amarillo" TT).
* **Análisis:** Se calculó el peso total del carro y el torque necesario para recuperar la verticalidad.
* **Justificación:** La relación de reducción de estos motores entrega el torque suficiente para mover la masa del robot con la agilidad requerida, descartando la necesidad de motores de mayor costo para esta escala de peso.

### 2. Sensorización (MPU6050)
Para el sistema de autobalance se optó por una IMU **MPU6050** (6 Grados de Libertad).
* **Datos obtenidos:** Aceleración lineal y Velocidad angular.
* **Justificación:** Se requiere fusión de sensores. El acelerómetro entrega la posición (inclinación) pero es ruidoso ante vibraciones; el giroscopio entrega la velocidad angular pero sufre de deriva (drift). Al combinar ambos datos obtenemos las variables de estado necesarias (Posición y Velocidad) para el controlador PID.

---

## Estructura del repositorio

A continuación se describe el contenido de las carpetas de este proyecto:

### 1. [`/CAD`](./CAD)
Contiene los archivos fuente para la fabricación del robot.
* **Archivos STL:** Listos para impresión 3D (Cabeza, Soportes de motor, Chasis base).
* **Ensamblaje:** Archivo de visualización del robot completo.
* *Nota: Se priorizó la robustez de la sujeción de los motores para evitar juegos mecánicos que afecten al PID.*

### 2. [`/Codigo`](./Codigo)
Firmware final cargado en el microcontrolador (Arduino/ESP32).
* **`main.ino`:** Archivo principal.
* **Librerías:** Se incluye referencia a la librería `MPU6050_tockn` (o la utilizada) y control de motores.
* *El código implementa un filtro complementario para la lectura del ángulo y un controlador PID discreto.*

### 3. [`/Diagramas`](./Diagramas)
Documentación esquemática del sistema.
* **Esquemático Electrónico:** Conexiones entre Drivers, MCU, IMU y alimentación.
* **Diagrama de Control:** Diagrama de bloques del lazo cerrado (Setpoint -> PID -> Planta -> Sensor).

### 4. [`/Componentes_y_materiales`](./Componentes_y_materiales)
Lista de materiales (BOM) y hojas de datos.
* `lista_materiales.pdf`: Resumen de costos y componentes.
* Datasheets principales (MPU6050, Driver de Motor, Motores DC con Encoder).

### 5. [`/Registros_audiovisuales`](./Registros_audiovisuales)
Evidencia del funcionamiento.
* Videos de pruebas de perturbación.
* Gráficas de respuesta del ángulo vs tiempo.
* Bitácora fotográfica del montaje.

---

## Arquitectura del sistema

### Hardware
* **Microcontrolador:** Arduino
* **Sensores:** IMU MPU6050 (Acelerómetro + Giroscopio)
* **Actuadores:** Motores DC con caja reductora.
* **Potencia:** Driver L298N y Baterías Li-Ion.

### Estrategia de Control
Se implementó un controlador **PID** sintonizado experimentalmente.
* **Setpoint:** 0° (Vertical).
* **Input:** Ángulo de inclinación filtrado (fusión de sensores).
* **Output:** PWM a los motores.

---

## Instrucciones de ejecución

1.  **Montaje:** Asegurar que la batería esté cargada y los cables de los motores firmemente conectados.
2.  **Calibración:** Al encender, mantener el robot estático verticalmente durante 5 segundos para la calibración del giroscopio.
3.  **Operación:** El robot intentará mantener el equilibrio automáticamente.
    * *Precaución: No operar en superficies resbaladizas.*

---

## Referencias

* **MPU6050 Datasheet:** (Enlace al Datasheet)
* **Librería MPU6050:** (Enlace al repo de la librería usada)
* **Documentación del Curso:** Requerimientos de Diseño ME4250 (Adjunto en repositorio).

---
*Este proyecto fue realizado con fines académicos para el Departamento de Ingeniería Mecánica de la Universidad de Chile.*
