# Task Estimator

# Problemática: 

Como desarrolladores de software nos vemos en la tarea de poder estimar cuánto tiempo nos podría tomar realizar tareas para poder llevar a cabo un proyecto, por lo general esta estimación suele alejarse de la realidad debido a múltiples factores o trabas en el proceso productivo así como también debido a las posibles variables que cambian durante el transcurso del mismo, no es un secreto que desarrollar software es complejo pero no imposible, por estas razones de que casi siempre se sale del tiempo estimado se convierte en un completo dolor de cabeza realizar un documento de estimación por que no suele cumplirse, ¿Por qué tomarse la molestia de trabajar en un calendario si no va a ser correcto? es la pregunta interna que se hace un desarrollador con pocos años de experiencia.

Lo que se suele aplicar en la actualidad es el uso de metodologías ágiles o frameworks de trabajo como lo puede ser Scrum, pero aun así nada es perfecto, qué tal si se pudiera utilizar una técnica de simulación de los proyectos basada en evidencia previa que nos permita tener mejores estimaciones? y no sólo estimaciones de tiempo sino de costos de un determinado proyecto y no perder dinero en el proceso.

Todo este tipo de problemas lo habrás sufrido en algún punto de tu vida profesional así es importante que se tenga en cuenta que usualmente un calendario de tareas medida en días o incluso semanas está condenado a no ser realista y más aún si quien lo realiza no esta asesorado por un desarrollador de software por lo que por recomendación divide las tareas en pequeños trozos que ocupen bloques menores a 16 horas de trabajo y que todo proceso estimado, y desarrollado se anote todo los acontecimientos y tiempo gastado a fin de poder al final tener una curva de distribución de confianza, una vez dicho esto es momento de poner manos a la obra para poder lograr este objetivo sin requerir aprender tantas cosas y que enseñarle a tu equipo sea sumamente sencillo.

# Definiciones de términos 

## Simulación de Montecarlo:

La simulación de Montecarlo es una técnica matemática computarizada que permite tener en cuenta el riesgo en el análisis cuantitativo y la toma de decisiones. La técnica es utilizada por profesionales de campos tan dispares como las finanzas, la gestión de proyectos, la energía, la fabricación, la ingeniería, la investigación y el desarrollo, los seguros, el petróleo y el gas, el transporte y el medio ambiente.

La simulación de Montecarlo proporciona al responsable de la toma de decisiones un abanico de posibles resultados y las probabilidades de que se produzcan para cualquier elección de acción. Muestra las posibilidades extremas -los resultados de ir a por todas y de la decisión más conservadora- junto con todas las posibles consecuencias de las decisiones intermedias.

La técnica fue utilizada por primera vez por los científicos que trabajaban en la bomba atómica; recibió el nombre de Montecarlo, la ciudad turística de Mónaco conocida por sus casinos. Desde su introducción en la Segunda Guerra Mundial, la simulación de Montecarlo se ha utilizado para modelar diversos sistemas físicos y conceptuales.


## Desviación Estándar:

Es una medida que se utiliza para cuantificar la variación o la dispersión de un conjunto de datos numéricos.

Una desviación estándar baja indica que la mayor parte de los datos de una muestra tienden a estar agrupados cerca de su media (también denominada el valor esperado), mientras que una desviación estándar alta indica que los datos se extienden sobre un rango de valores más amplio.

## Mediana:

En el ámbito de la estadística, la mediana (del latín mediānus del medio​) representa el valor de la variable de posición central en un conjunto de datos ordenados. Se le denomina mediana.

Si la serie tiene un número par de puntuaciones, la mediana es la media entre las dos puntuaciones centrales


## Límites en Estadística:

Son los valores extremos que tiene el intervalo de clase, inferior y superior, entre los cuales van a estar los valores de los datos agrupados en ese intervalo de clase.


# Notas:
> Con la simulación de Montecarlo tal como se conoce es posible probar distintos escenarios posibles, para este proyecto realizado se tomó en cuenta en base a 100 posibles escenarios del futuro basado en los siguientes datos, tiempo mínimo, tiempo máximo, nivel de confianza y costo por hora y considerando que cada uno de estos futuros tiene un 1% de posibilidad de darse.


## Recomendaciones

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Configuraciones

Ver [Vite Configuration Reference](https://vitejs.dev/config/).

## Instalación

```sh
npm install
```

### Compilar y Hot-Reload

```sh
npm run dev
```

### Compilar y Minificar para Producción

```sh
npm run build
```
