# Aprendizaje supervisado :rocket:

En este proyecto, además de entrenar varios modelos, se estandarizan y codifican los datos para obtener mejores resultados en las métricas de evaluación del modelo

## Descripción del proyecto
Tenemos unn dataset con información de los clientes del banco BetaBank, los cuales se están yendo mes con mes. Los banqueros descubrieron que es más barato salvar a los clientes existentes que atraer nuevos.

La tarea es predecir si un cliente dejará el banco pronto. Dentro de los datos se tiene el comportamiento pasado de los clientes y la terminación de contratos con el banco.

## Objetivo
Al revisar el dataset se sabe que este contiene una columna que indica si el cliente se ha ido (ha terminado el contrato con el banco) con un 1 y con 0 los clientes que siguen teniendo un cotrato. Con esto podemos decir que la tarea es de clasificación binaria.

Se pide que se cree un modelo con el máximo valor F1 posible. Para aprobar la revisión, es necesario un valor F1 de al menos 0.59.

## Desarrollo del proyecto
### Descarga y preparación de los datos.
Se importaron los datos utilizando Pandas revisando si hay valores ausentes o duplicados y se explica como se procesaron. Además se explica la eliminación de columnas que no contienen información útil para el modelo

En esta sección se hce una codificación One Hot (OHE). Este tipo de codificación transforma las características categóricas en numéricas. 

Al tratarse de una tarea de clasificación, también se realiza un escalado de características. Con esto nos aseguramos de que el modelo considere a todas las características igual de importantes.

### Entrenamiento del modelo
Se sabe que hay un claro desequilibrio de clases, ya que hay un mayor número de ceros (clientes con contrato) que de unos.

Sin tomar en cuenta esto, se entrenan los modelos de: Árbol de decisión, bosque aleatorio y regresión logística. Y se saca su valor F1.

Posteriormente se realiza balnceo de clases utilizando dos técnicas:
1. Submuestreo: hace que las observaciones de una clase frecuente, sean menos frecuentes.
2. Sobremuestreo: hace que las observaciones de una clase no tan frecuente, se vuelvan más frecuentes.

Después de realizar estás técnicas se vuelven a entrenar los modelos, utilizando estos nuevos datos y obtenemos el valor F1 de cada modelo.

## Conclusiones
El valor más cercano a 0.59 se encontró con el modelo de bosque aleatorio utilizando el conjunto de sobremuestreo con un valor de F1 = 0.589, por lo tanto este es el modelo que se ocupará para el conjunto de prueba. Sin embargo, al evaluar el conjunto de prueba usando este modelo, el valor F1 es de 0.513.
