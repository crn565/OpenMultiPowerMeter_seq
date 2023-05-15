# OpenMultiPowerMeter_seq

Muestras secuenciales de 5 electrodomesticos más el agregado usando el OMPM  (equipo de medida propio  basados en un bus RS485 con modulos PZEM004) el dia 13 de Mayo de 2023
entre  las 17:22 y las 23:43 completando  en total 6h 21 minutos de muestras.

No hay pausa entre secuencias y el tiempo de encendido de cada secuencia es seudoaleatorio entre 1  y 2 minutos. Esto difiere de un experimento anterior en el que la secuencia tambien fue ascendente pero el encendido y apagado de los electrodomesticos se hizo manualmente.

El periodo de entrenamiento,validacion  y test  se hace en la proporcion 60/20/20, es decir: 

- Entrenamiento :de 17:22 a 21:08

- Validacion : de 21:08 a 22:35

- Test: de 22:35 a 23:43

# Resultados Metricas  con algoritmo CO, metodo Median  y 10"

## Datos anteriores con secuencia fija y tiempo de encendido fijo de 2 minutos

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
| F1              | 0.420   | 0.789    | 0.756            | 0.453           | 0.741   | 0.632            |
| EAE            | 0.002   | 0.001    | 0.011            | 0.002           | 0.012   | 0.006            |
| MNEAP       | 1.138   | 0.349    | 0.484            | 1.150           | 0.502   | 0.725            |
| RMSE        | 17.417 | 7.339     | 22.688         | 13.816         | 12.651 | 14.382           |



## Datos con muestras aleatorias 

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
| F1              | 0.591   | 0.158    | 0.752            | 0.349           | 0.577   | 0.485            |
| EAE            | 0.000 | 0.005   | 0.005             | 0.003          | 0.001  | 0.002             |
| MNEAP       | 0.726   | 1.596     | 0.443            | 1.212           | 0.823   | 0.960            |
| RMSE        | 11.169 | 9.259     | 18.718          | 8.170           | 15.660 | 12.995           |



## Datos  en secuencia fija con programador  y tiempo de encendido seudoaleatorio entre 10 y 60 segundos

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
|F1|	0.638	|0.364|	0.858|	0.381|	0.682	|0.5846|
|EAE|	0.000|	0.000	|0.000|	0.000|	0.000|	0.0000|
|MNEAP|	0.678	|1.391|	0.342|	1.343|	0.761|	0.9030|
|RMSE	|11.315|	9.334	|15.782|	8.833|	15.806|	12.2146|

## INTERPRETACION DE LOS RESULTADOS

### Solo considerando la matrica F1

El mejor resultado es el que tiene la puntuación F1 más alta, que son los datos secuenciales con secuencia fija y tiempo de encendido fijo. La puntuación F1 es una medida de exactitud que tiene en cuenta tanto la precisión como la recuperación. La precisión es la fracción de casos positivos predichos que son realmente positivos, y la recuperación es la fracción de casos positivos reales que son positivos predichos. Cuanto mayor sea la puntuación F1, más precisa será la predicción.


Los otros dos resultados no son tan buenos porque tienen puntuaciones F1 más bajas. Los datos con muestras aleatorias tienen una puntuación F1 de 0,485, y los datos de secuencias con muestras aleatorias tienen una puntuación F1 de 0,5846. Estos resultados no son tan buenos como los de los datos de secuencia con secuencia fija porque son menos precisos.

La razón por la que los datos de secuencia con secuencia fija son más precisos es que es más fácil predecir el consumo de energía de los electrodomésticos cuando se conoce la secuencia de eventos que ocurrieron en la casa. Por ejemplo, si se sabe que alguien encendió el horno a las 18:00, se puede predecir que el horno consumirá más energía a esa hora. Esto no es posible con los otros dos conjuntos de datos porque no contienen información sobre la secuencia de acontecimientos.

En conclusión, el mejor resultado es el que tiene la puntuación F1 más alta, que son los datos con secuencia fija. Este resultado es más preciso porque tiene en cuenta la secuencia de acontecimientos que ocurrieron en la casa.

### Considerando todas la metricas


Para determinar cuál de los tres conjuntos de resultados de las métricas NILMTK es el mejor, tenemos que considerar qué métricas son las más importantes para el caso de uso específico.

Si damos prioridad a la puntuación F1, que es una medida de la precisión global del algoritmo NILM, podemos ver que el conjunto de datos de secuencia tiene la puntuación F1 más alta para todos los aparatos excepto para la lámpara LED. Sin embargo, si consideramos todos los aparatos juntos, el conjunto de datos anterior con secuencia fija tiene la puntuación F1 media más alta.

Si priorizamos la métrica RMSE, que mide el error entre el consumo de energía real y el predicho, podemos ver que los datos con muestras aleatorias tienen el RMSE más bajo para todos los aparatos excepto para la Lámpara LED.

Si priorizamos la métrica MNEAP, que mide el error medio normalizado en la potencia de los aparatos, podemos ver que el conjunto de datos anterior con secuencia fija tiene el MNEAP más bajo para todos los aparatos excepto para el Ordenador Portátil.

En general, la elección del mejor conjunto de resultados de la métrica NILMTK dependerá del caso de uso específico y de la prioridad de las distintas métricas.

