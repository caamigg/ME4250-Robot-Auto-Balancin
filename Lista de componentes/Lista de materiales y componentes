# Lista de materiales y componentes

Este documento detalla el hardware, electrónica y piezas mecánicas utilizadas en el proyecto **Wall-E Balancer**.

## 1. Electrónica de Control y Potencia

| Componente | Imagen Referencial | Descripción Técnica | Documentación |
| :--- | :---: | :--- | :---: |
| **Arduino Uno R3** | <img src="./Lista de componentes/Imágenes componentes/MCI00756A.png" width="100"> | Microcontrolador basado en ATmega328P. Cerebro del sistema encargado de leer el sensor y ejecutar el PID. | [Ver Datasheet](./Datasheets/Arduino_Uno_Schematic.pdf) |
| **Driver L298N** | <img src="./Lista de componentes/Imágenes componentes/L298N_driver.png" width="100"> | Puente H Dual. Permite controlar el sentido y velocidad (PWM) de los dos motores DC utilizando una fuente de voltaje externa. | [Ver Datasheet](./Datasheets/L298N_datasheet.pdf) |
| **IMU MPU6050** | <img src="./Lista de componentes/Imágenes componentes/MPU6050.jpg" width="100"> | Sensor de 6 Grados de Libertad (6-DOF). Combina un acelerómetro de 3 ejes y un giroscopio de 3 ejes con procesador de movimiento digital (DMP). | [Ver Datasheet](./Datasheets/MPU6050_Datasheet.pdf) |

## 2. Alimentación y Actuadores

| Componente | Imagen Referencial | Descripción Técnica | Documentación |
| :--- | :---: | :--- | :---: |
| **Motores DC con Reductora** | <img src="./Lista de componentes/Imágenes componentes/Motor-DC.png" width="100"> | Motor tipo TT (Amarillo) con caja reductora 1:48. Torque aprox: 0.8 kg·cm. Voltaje op: 3V-6V. | [Ver Specs](./Datasheets/TT_Motor_Specs.pdf) |
| **Baterías Li-Ion 18650** | <img src="./Lista de componentes/Imágenes componentes/Li-ion-Batteries-18650.png" width="100"> | 2 celdas de 3.7V conectadas en serie (7.4V total). Alta capacidad de descarga para los motores. | - |
| **Portapilas 18650** | <img src="./Lista de componentes/Imágenes componentes/Portapilas.png" width="100"> | Soporte para 2 baterías en serie con cables de salida. | - |
| **Interruptor** | <img src="./Lista de componentes/Imágenes componentes/Interruptor.png" width="100"> | Switch ON/OFF tipo palanca para corte general de energía. | - |

## 3. Conexiones y Estructura

* **Cables Jumper:**
    * *Macho-Macho:* Para conexiones entre Arduino y Driver L298N.
    * *Macho-Hembra:* Para conexión del sensor MPU6050 al Arduino.

## 4. Piezas Fabricadas (Impresión 3D)

Las piezas fueron diseñadas en CAD y fabricadas utilizando **PLA Genérico** (Ácido Poliláctico) con una densidad de relleno del 20%.

| Pieza | Función | Archivo Fuente |
| :--- | :--- | :---: |
| **Cabeza Wall-E** | Estética y contrapeso superior para elevar el Centro de Masa. | [Ver STL](../CAD/Cabeza Wall-e.stl) |
| **Chasis Principal** | Base estructural que aloja las baterías y soporta el Arduino. | [Ver STL](../CAD/Carcasa.stl) |
| **Ruedas** | Permiten el deslizamiento del carro por distintas superficies. | [Ver STL](../CAD/Ruedas.stl) |

