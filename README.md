# OpenMultiPowerMeter_seq
# openMultiPowerMeter_random
Muestras secuenciales de 5 electrodomesticos más el agregado usando el OMPM  (equipo de medida propio  basados en un bus RS485 con modulos PZEM004) el dia 13 de Mayo de 2023
entre  las 17:22 y las 23:43 completando  en total 6h 21 minutos de muestras.

No hay pausa entre secuencias y el tiempo de encendido de cada secuencia es seudoaleatorio entre 1  y 2 minutos

El periodo de entrenamiento,validacion  y test  se hace en la proporcion 60/20/20, es decir : 

- Entrenamiento :de 14:49 a 16:19

- Validacion : de 16:19 a 17:13

- Test: de 17:13 a 18:07

# Resultados Metricas  con algoritmo CO, metodo Median  y 10"

## Datos anteriores con secuencia fija

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
| F1              | 0.420   | 0.789    | 0.756            | 0.453           | 0.741   | 0.632            |
| EAE            | 0.002   | 0.001    | 0.011            | 0.002           | 0.012   | 0.006            |
| MNEAP       | 1.138   | 0.349    | 0.484            | 1.150           | 0.502   | 0.725            |
| RMSE        | 17.417 | 7.339     | 22.688         | 13.816         | 12.651 | 14.382           |



## Datos actuales con muestras aleatorias 

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
| F1              | 0.591   | 0.158    | 0.752            | 0.349           | 0.577   | 0.485            |
| EAE            | 0.000 | 0.005   | 0.005             | 0.003          | 0.001  | 0.002             |
| MNEAP       | 0.726   | 1.596     | 0.443            | 1.212           | 0.823   | 0.960            |
| RMSE        | 11.169 | 9.259     | 18.718          | 8.170           | 15.660 | 12.995           |



##



